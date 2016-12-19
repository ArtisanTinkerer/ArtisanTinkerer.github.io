---
layout: default
title: "Datamax Label Printing"
date: 2016-06-07
---

# The PHP


```
    private $socket;
    private $port = "9100";
    private  $host = "10.0.4.151";
    
    function testLabel()
    {
        $this->opensocket();
        //this file tells the printer it is getting an image to store
        $this->sendFile("assets/images/testHeader.txt");
        //standard bitmap
        $this->storeImage("assets/images/2 Cup.bmp");
        //send the command to the printer to print the label        
        $this->writeLabel();

        $this->closesocket();

    }
    
    function opensocket (){
        $this->socket = socket_create(AF_INET, SOCK_STREAM, 0);
        if ($this->socket === false) {
            echo "socket_create() failed: reason: " . socket_strerror(socket_last_error()) . "\n";
        } else {
            echo "OK.\n";
        }
        $result = socket_connect($this->socket, $this->host, $this->port);
        if ($result === false) {
            echo "socket_connect() failed.\nReason: ($result) " . socket_strerror(socket_last_error($this->socket)) . "\n";
        } else {
            echo "OK.\n";
        }

    }


    function storeImage ($filename){
        $image = file_get_contents($filename) ;
        socket_write($this->socket, $image, strlen($image));

    }


    function sendFile ($filename){
        if (file_exists($filename)) {
            $fd = fopen($filename, 'r');
            if ($fd) {
                $data = fread($fd, filesize($filename));
                fclose($fd);
            }
        }
        socket_write($this->socket, $data, strlen($data));
    }


    function writeLabel()
    {

        $STX = Chr(2);
        $SOH = Chr(1);

        $PNBC = "123456";
        $PN = "123456";
        $Quantity = "0001";

        $command = "L
        ";
        $command .= "D11
            ";
        $command .= "ySW1
        A2
        2911S0105800357P012P012Company Name
        2eE710403680042B$PNBC
        2911S0102410027P012P012$PNBC

        2911S0105750296P012P012Part No:
        2911S0105120297P012P012$PN
        1Y1100000130269test
        Q$Quantity
        E
        ";
        socket_write($this->socket, $command, strlen($command));
    }

    function closeSocket (){
        socket_close($this->socket);

    }
    
```  
 
 
 
## The command to store the image
    <STX>n<CR><LF>
    <STX>M1500<CR><LF>
    <STX>V0<CR><LF>
    <STX>ICBtest<CR><LF>

