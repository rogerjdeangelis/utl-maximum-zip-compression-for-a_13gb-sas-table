# utl-maximum-zip-copression-for-a_13gb-sas-table
Maximum zip compression for a 13gb sas table  
    Maximum zip copression for a 13gb sas table                                                                                       
                                                                                                                                      
    System                                                                                                                            
                                                                                                                                      
      $800 Dell T7610, 32 logical cores, 128gb, dual nvme drives.                                                                     
                                                                                                                                      
    Benchmark                                                                                                                         
                                                                                                                                      
       ZIP                                                                                                                            
                                                                                                                                      
         Input  13gb SAS table                                                                                                        
         Output 32mb zip file                                                                                                         
         Elapsed time 216 seconds                                                                                                     
                                                                                                                                      
       UNZIP                                                                                                                          
                                                                                                                                      
         Input  32mb zip file                                                                                                         
         Output 13gb SAS table                                                                                                        
         Elapsed time 12 seconds                                                                                                      
                                                                                                                                      
    Notes                                                                                                                             
                                                                                                                                      
      Not that slow, if you have 24 logical cores (7-zip can peg 24 cores)                                                            
      Fastest unzip                                                                                                                   
                                                                                                                                      
    github                                                                                                                            
    https://tinyurl.com/y4e7l4wm                                                                                                      
    https://github.com/rogerjdeangelis/utl-maximum-zip-compression-for-a_13gb-sas-table                                               
                                                                                                                                      
    github (for comparison of techniques)                                                                                             
    https://tinyurl.com/yxoh2psg                                                                                                      
    https://github.com/rogerjdeangelis/utl-zip-and-unzip-comparisons-using-bzip2-gzip_7-zip-and-sas-zip                               
                                                                                                                                      
    SAS Forum                                                                                                                         
    https://tinyurl.com/yxkyb89n                                                                                                      
    https://communities.sas.com/t5/SAS-Programming/How-to-Compress-a-SAS-dataset-and-Extract-and-Open-in-Windows/m-p/693358           
                                                                                                                                      
    /*                   _                                                                                                            
    (_)_ __  _ __  _   _| |_                                                                                                          
    | | `_ \| `_ \| | | | __|                                                                                                         
    | | | | | |_) | |_| | |_                                                                                                          
    |_|_| |_| .__/ \__,_|\__|                                                                                                         
            |_|                                                                                                                       
    */                                                                                                                                
                                                                                                                                      
    libname sd1 "d:/sd1";                                                                                                             
                                                                                                                                      
    * 13 GB;                                                                                                                          
    libname sd1 "d:/sd1";                                                                                                             
    data sd1.have;                                                                                                                    
      set sashelp.cars;                                                                                                               
      do rec=1 to 187500;                                                                                                             
        output;                                                                                                                       
      end;                                                                                                                            
    run;quit;                                                                                                                         
                                                                                                                                      
    7-zip switch                                                                                                                      
                                                                                                                                      
    Switch -mx9: This means "ultra" compression.                                                                                      
                 You probably want to use this.                                                                                       
                                                                                                                                      
    Data Set Name         SD1.HAVE                                                                                                    
                                                                                                                                      
    Observations          80250000                                                                                                    
    Variables             16                                                                                                          
    Observation Length    160                                                                                                         
    Compressed            NO                                                                                                          
                                                                                                                                      
    Data Set Page Size          65536                                                                                                 
    Number of Data Set Pages    196211                                                                                                
    First Data Page             1                                                                                                     
    Max Obs per Page            409                                                                                                   
    Obs in First Data Page      392                                                                                                   
    Filename                    d:\sd1\have.sas7bdat                                                                                  
    File Size (bytes)           12858949632                                                                                           
                                                                                                                                      
    /*           _               _                                                                                                    
      ___  _   _| |_ _ __  _   _| |_                                                                                                  
     / _ \| | | | __| `_ \| | | | __|                                                                                                 
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                  
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                 
         _          |_|                                                                                                               
     ___(_)_ __                                                                                                                       
    |_  / | `_ \                                                                                                                      
     / /| | |_) |                                                                                                                     
    /___|_| .__/                                                                                                                      
          |_|                                                                                                                         
    */                                                                                                                                
                                                                                                                                      
    d:/zip/have13gb.7z                                                                                                                
                                                                                                                                      
      38.4 MB (40,349,696 bytes)                                                                                                      
                                                                                                                                      
    Elapsed time                                                                                                                      
                                                                                                                                      
    Seconds 216.414000034332                                                                                                          
    size    40mb                                                                                                                      
                                                                                                                                      
    /*               _                                                                                                                
     _   _ _ __  ___(_)_ __                                                                                                           
    | | | | `_ \|_  / | `_ \                                                                                                          
    | |_| | | | |/ /| | |_) |                                                                                                         
     \__,_|_| |_/___|_| .__/                                                                                                          
                      |_|                                                                                                             
    */                                                                                                                                
    Data Set Name         SD1.HAVE                                                                                                    
                                                                                                                                      
    Observations          80250000                                                                                                    
    Variables             16                                                                                                          
    Observation Length    160                                                                                                         
    Compressed            NO                                                                                                          
                                                                                                                                      
    Data Set Page Size          65536                                                                                                 
    Number of Data Set Pages    196211                                                                                                
    First Data Page             1                                                                                                     
    Max Obs per Page            409                                                                                                   
    Obs in First Data Page      392                                                                                                   
    Filename                    d:\sd1\have.sas7bdat                                                                                  
    File Size (bytes)           12858949632                                                                                           
                                                                                                                                      
    /*                                                                                                                                
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|                                                                                               
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                               
    | .__/|_|  \___/ \___\___||___/___/                                                                                               
    |_|  _                                                                                                                            
     ___(_)_ __                                                                                                                       
    |_  / | `_ \                                                                                                                      
     / /| | |_) |                                                                                                                     
    /___|_| .__/                                                                                                                      
          |_|                                                                                                                         
    */                                                                                                                                
                                                                                                                                      
                                                                                                                                      
    */                                                                                                                                
                                                                                                                                      
    %let tym=%sysfunc(datetime());                                                                                                    
                                                                                                                                      
    x "C:\Progra~1\7-Zip\7z a -mx9 -mmt -t7z d:/zip/have13gb.7z d:/sd1/have.sas7bdat";                                                
                                                                                                                                      
    %put %sysevalf(%sysfunc(datetime()) - &tym);                                                                                      
                                                                                                                                      
    Seconds 216.414000034332                                                                                                          
    size    40mb                                                                                                                      
                                                                                                                                      
                                                                                                                                      
    /*               _                                                                                                                
     _   _ _ __  ___(_)_ __                                                                                                           
    | | | | `_ \|_  / | `_ \                                                                                                          
    | |_| | | | |/ /| | |_) |                                                                                                         
     \__,_|_| |_/___|_| .__/                                                                                                          
                      |_|                                                                                                             
    */                                                                                                                                
                                                                                                                                      
                                                                                                                                      
    %utlfkil(d:/sd1/have.sas7bdat);                                                                                                   
                                                                                                                                      
    %let tym=%sysfunc(datetime());                                                                                                    
                                                                                                                                      
    x "C:\Progra~1\7-Zip\7z e d:/zip/have13gb.7z -od:/sd1";                                                                           
                                                                                                                                      
    %put %sysevalf(%sysfunc(datetime()) - &tym);                                                                                      
                                                                                                                                      
    libname sd1 "d:/sd1";                                                                                                             
    proc contents data=sd1.have;                                                                                                      
    run;quit;                                                                                                                         
                                                                                                                                      
    Seconds 11.8489999771118                                                                                                          
    size    13gb                                                                                                                      
                                                                                                                                      
                                                                                                                                      
                                                                                                                                      
