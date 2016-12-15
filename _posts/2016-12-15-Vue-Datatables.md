---
layout: post
title: "Creating a Datatables Vue Component"
date: 2016-12-15
---

# Creating a Datatables Vue Component

Since I am currently learning Vue.js, I decided to create a component for Datatables. Obviously using Laravel.

## Progress

I still have a lot to do, but the basics are working.
Not really happy with the way I am doing the buttons, these need to be added based on the users permissions.



HTML:

```
    <div id="app">
        <ch-datatable  table-url="/widgetsTable" data-url="/widgetsAjax">    </ch-datatable>
    </div> {{--app--}}
    
```   
    
    
  Controller:
  
```
  public function tableSetup()
    {
        $dt = new Datatable("widgets", "Widgets");//table and panel title

        $dt->fieldTitles = array('Title', 'Description');
        $dt->dbFields = array('title', 'description');

        return $dt->createResponse();
    }
    
    public function datatablesAjax()
    {
        global $db;//this is needed to get Datatables to work with Laravel

        $postData = $_POST;

        Editor::inst($db, 'widgets')
            ->fields(
                Field::inst("widgets.id"),
                Field::inst('widgets.title'),
                Field::inst("widgets.description")
            )
            ->process($postData)
            ->json();
    }
}
  
```
 
 
 I hate the way I am building these arrays to make the response.
 
 My Datatables Class:
 
```
 class Datatable
{
    private $dbTable;
    private $panelTitle;

    public $fieldTitles;
    public $dbFields;

    public function __construct($dbTable, $panelTitle)
    {
        $this->dbTable = $dbTable;
        $this->panelTitle = $panelTitle;
    }


    public function createResponse()
    {

        $arrResponse = array();

        $arrResponse['panelTitle'] = $this->panelTitle;
        $arrResponse['table'] = $this->dbTable;

        $arrEditorDescriptions = $this->fieldTitles;

        array_unshift($this->fieldTitles, ''); //first column is needed for the checkbox
        $arrTableHeaders = $this->fieldTitles;

        $arrTableColumns = $this->dbFields;


        //first lets set up the HTML table ---------------------------------------------------------------
        $arrResponse['tableHeaders'] = $arrTableHeaders;

        //now the editor fields----------------------------------------------------------------------------

        $numColumns = sizeof($arrEditorDescriptions);
        for ($field = 0; $field < $numColumns; $field++) {
            $arrResponse['editorFields'][] = ['label' => $arrEditorDescriptions[$field], 'name' => $arrResponse['table'] . '.' . $arrTableColumns[$field]];
        }

        //editor is done, now lets sort the table out------------------------------------------------------

        //this is the first one which is a checkbox for selecting
        $arrResponse['tableColumns'][] = ['data' => "null", 'className' => 'select-checkbox', 'orderable' => false, 'defaultContent' => ''];

        $numColumns = sizeof($arrTableColumns);
        for ($field = 0; $field < $numColumns; $field++) {
            $arrResponse['tableColumns'][] = ['data' => $arrResponse['table'] . '.' . $arrTableColumns[$field]];
        }

        return response()->json($arrResponse);
    }


}
 
```
 
 and here is the Vue component:
 
```
 <template>
    <div class="container">
        <div class="panel panel-primary">
            <div class="panel-heading" id="panel-head">
                {{panelTitle}}
            </div>
            <div class="panel-body">
                <table class="table table-responsive" id="datatables-table">
                    <thead>
                    <tr>
                        <th v-for="header in tableHeaders">
                            {{header}}
                        </th>
                    </tr>
                    </thead>

                </table>
            </div>
        </div>
    </div>
</template>


<script>
//add permission stuff

    export default {
        props: ['dataUrl','tableUrl'],
         data() {
          return {

            tableHeaders: [],
            panelTitle: "",
            table:"",
            editorFields: [],
            tableColumns: [],
            edit:false,
            buttons:"",
            columnDefs: "",
            rowCallBack: "",
            extraJS: "",
            }
        },

        mounted: function () {
         let self = this;

        axios.get(self.tableUrl)
            .then(function (response) {

                self.tableHeaders = response.data.tableHeaders;
                self.panelTitle = response.data.panelTitle;
                self.table = response.data.table;
                self.editorFields = response.data.editorFields;
                self.tableColumns = response.data.tableColumns;
                self.buttons = response.data.buttons;


            })
            .catch(function (error) {
                console.log(error);
            });

        },

       updated: function () {

        let self = this;

         //setup the editor
       let editor = new $.fn.dataTable.Editor({
                 "ajax": {
                "url": self.dataUrl,
                "type": "POST",
                data: {table: self.table}
            },

    table: "#datatables-table",
    idSrc: self.table + '.id',
    fields: [self.editorFields]
        });


         //setup the Datatable
        let table = $('#datatables-table').DataTable({ //took the var off to intentionally make it global

            "ajax": {
                "url": self.dataUrl,
                "type": "POST",

                "data": function(d){
                    d.table = self.table;
                },

            },


        "columns": self.tableColumns,
            order: [1, 'asc'],
            dom: "Bfrtip",
            responsive: false,//true wont let me hide columns
            "scrollY": "600px",
            "scrollCollapse": true,

            "paging": false,
            select: {
                style: 'single',
                selector: 'td:first-child',
                blurable: true

            },

            buttons: [{extend:'remove', editor: editor},{extend:'create', editor: editor},{extend:'edit', editor: editor}],

        });
    }

    }

</script>

 
 ```
 
 
