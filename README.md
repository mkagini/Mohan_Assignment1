#!/bin/sh

#set the counter variables for Row,Collumn and File 

colcnt=1
rowcnt=1
filecnt=1

    #delete files created earlier

cleanup()

    {
     rm input_File *assignment1*

     }

  # Creating 50 rows before converting to columns

 createColumns()
    {
  
    while [["$colcnt" -le 50]]
       do
       echo column_$colcnt >> input_file
            colcnt=$((colcnt+1)
     done
# convert rows to columns
    Awk '{printf"%s\t",$1}'input_file > input_file.temp
    echo "50 collumns created"
    }
 # create 1000 rows with the above 50 collumns
    createFile()
      {
        newcnt=$1
        rowcnt=1
       while [["$rowcnt" -le 1000]]
         do 
         cat input_file.temp >> Mohan_Assignment_$newcnt.out
                   rowcnt=$((rowcnt+1))
                   echo "\n" >> Mohan_Assignment_$newcnt.out
               done   
  echo "created file Mohan_Assignment_$newcnt.out"
   }
 # The following program creates 10000 files 
     cleanup
      while [["$filecnt" -le 10000]]
               do 
              createFile  $filecnt
              filecnt=$((filecnt+1))
       done
   echo "10000 files created.   
      
  # Mohan_Assignment1
unix shell script to create 10000 files with 10000 records in easch file with 50 collumns and copy to HDFS
