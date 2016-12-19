---
layout: default
title: "Taming an Excel Monster"
date: 2016-03-10
---

## Simple Spreadsheets Evolve Into Monsters 

So, I will tame then with the help of PHP Excel

1. Install by adding this to Composer.json "phpoffice/phpexcel": "1.8.0"
2. Composer Update
```
 
/**  Define a Read Filter class implementing PHPExcel_Reader_IReadFilter  */
class MyReadFilter implements \PHPExcel_Reader_IReadFilter
{
    public function readCell($column, $row, $worksheetName = '') {
        //  Read rows 1 to 7 and columns A to E only
        if ($row >= 1 && $row <= 7) {
            if (in_array($column,range('A','E'))) {
                return true;
            }
        }
        return false;
    }
}


$destinationPath = 'uploads'; // upload path
            $extension = Input::file('glazing')->getClientOriginalExtension(); // getting image extension
            $fileName = rand(11111,99999).'.'.$extension; // renaming image

            Input::file('glazing')->move($destinationPath, $fileName); // uploading file to given path


        //lets fire up PHPExcel and see what it can do
        $inputFileName = "$destinationPath/$fileName";

        /**  Identify the type of $inputFileName  **/
        $inputFileType = \PHPExcel_IOFactory::identify($inputFileName);

        /**  Create an Instance of our Read Filter  **/
        $filterSubset = new MyReadFilter();
        
         /**  Create a new Reader of the type that has been identified  **/
        $objReader = \PHPExcel_IOFactory::createReader($inputFileType);
        /**  Advise the Reader that we only want to load cell data  **/
        $objReader->setReadDataOnly(true);

        $sheetname = "plan";


        /**  Advise the Reader of which WorkSheets we want to load  **/
        $objReader->setLoadSheetsOnly($sheetname);

        /**  Tell the Reader that we want to use the Read Filter  **/
        $objReader->setReadFilter($filterSubset);





        try {
            /** Load $inputFileName to a PHPExcel Object  **/
            $objPHPExcel = \PHPExcel_IOFactory::load($inputFileName);
        } catch(\PHPExcel_Reader_Exception $e) {
            die('Error loading file: '.$e->getMessage());
        }
        
```
        
        
## Then I did some tinkering.
        
        
```
        $sheet = $objPHPExcel->getActiveSheet();
        $sheet->getCell('C1')->getValue();
```
        
        
        Looks like I can get the data out!
        
        $objPHPExcel->setActiveSheetIndex(0)->getHighestRow();

        
        
 [link Reading] (https://github.com/PHPOffice/PHPExcel/blob/681c30b2ea3871ba8d9e484b4400edccba377ee0/Documentation/markdown/Overview/07-Accessing-Cells.md)
        
# The Old Conundrum
 
 Looks like I need to use:
 
        getOldCalculatedValue
        
 Otherwise, I get the forumla! 
 
 This converned me for a while, until I read this:
 
 However - Note that when you save a workbook in MS Excel itself, it calculates the result for all formulae and stores the result in the workbook. This is the result returned by getOldCalculatedValue(). However, not all spreadsheet programs do this: OOCalc does; Gnumeric doesn't; Multiplan (SYLK) or CSV files don't hold this old calculated value either. If the loaded workbook hasn't done this calculation on save, then getOldCalculatedValue() will return a null.

So basically getOldCalculatedValue gets a value which Excel has cached.


        
        
 
 
        
        
