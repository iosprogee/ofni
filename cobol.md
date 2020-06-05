#### [cobol](https://consulting-bolte.de/index.php/tech-blog/cobol/184-install-cobol-on-macos-x)
#### [tutorial](https://riptutorial.com/cobol)
#### install compiler
```
 $ brew install gnu-cobol
 $ brew install pyqt5      ##--using python3
 $ pip3 install PyQt5
```
####  install ide & run
```
 $ pip3 install OpenCobolIDE --upgrade
 $ openCobolIde
```
####  compile hello.cbl output executable to folder bin
```
 $ cobc -free -x -o bin/helloworld hello.cbl
```
#### looper  
```
 IDENTIFICATION DIVISION.
 PROGRAM-ID. LOOPER.
 DATA DIVISION.
 WORKING-STORAGE SECTION.
    01 WS-CNT PIC 9(1) VALUE 1.
    01 W2-CNT PIC 9(1) VALUE 1.

 PROCEDURE DIVISION.
    MAIN-1.
    PERFORM FN-DISP WITH TEST AFTER UNTIL WS-CNT>3.
    STOP RUN.

    FN-DISP.
    DISPLAY 'WS-CNT : ',WS-CNT,","W2-CNT.
    ADD 1 TO WS-CNT.

 END PROGRAM LOOPER.
```