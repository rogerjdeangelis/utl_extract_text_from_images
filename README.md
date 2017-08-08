# utl_extract_text_from_images
Extract text imbeded inside images into clear text in a file

    ```  Convert text inside images to clear text  ```
    ```    ```
    ```  example input ( Tried to provide weak and atrong text representations0  ```
    ```  https://www.dropbox.com/s/0utaoicslu0t57u/bmp.bmp?dl=0  ```
    ```    ```
    ```  example output  ```
    ```  https://www.dropbox.com/s/2cz2r6r7xneedk9/bmp.txt?dl=0  ```
    ```    ```
    ```    ```
    ```    WORKING CODE  ```
    ```    ```
    ```        Use SAS Code to create an BMP image.  ```
    ```        %tesser(device=bmp,type=bmp);  ```
    ```    ```
    ```        * Convert text in image to text;  ```
    ```        * this command is inside the macro above;  ```
    ```        x c:/progra~2/tesseract-ocr/tesseract d:/tesser/slide.bmp d:/tesser/slide.txt;  ```
    ```    ```
    ```    ```
    ```  Adminstrative information  ```
    ```    ```
    ```  Where I originally got the tesseract package  ```
    ```  https://github.com/UB-Mannheim/tesseract/wiki  ```
    ```    ```
    ```  There is GUI available and you get a console with both distributions.  ```
    ```  I did not install the GUI.  ```
    ```    ```
    ```  Also located on my google drive(use this before they do a SAS like enhancement)  ```
    ```  https://drive.google.com/file/d/0ByX2ii2B0Rq9MmZmVVNjLXpNdkU/view?usp=sharing  ```
    ```    ```
    ```  Need this to handle PDFs  ```
    ```  Get ghostscript here (note ghostscript can combine PDF files and can convert PDF to TIF.  ```
    ```  http://www.ghostscript.com/download/gsdnld.html  ```
    ```  Really only need one executable.  ```
    ```    ```
    ```    ```
    ```    ```
    ```  HAVE SIX IMAGE FILES I NEED TO EXTRACT THE TEXT  ```
    ```  ===============================================  ```
    ```    ```
    ```  I have these image files  ```
    ```    ```
    ```   png.png  ```
    ```   bmp.bmp  ```
    ```   jpg.jpg  ```
    ```   tiff.tiff  ```
    ```   gif.gif  ```
    ```    ```
    ```   pdftif.tiff  (you need to convert the PDF to an Image file)  ```
    ```    ```
    ```    ```
    ```  IMAGE LOOKS LIKE (from proc gslide)  ```
    ```    ```
    ```  MYSTUDY C304456                               AJAX  ```
    ```  DRAFT                                             VER 1.0  ```
    ```    ```
    ```                        Ajax Study  ```
    ```                     Dose and Placebo  ```
    ```    ```
    ```                           NOTE1  ```
    ```                           NOTE2  ```
    ```                           NOTE3  ```
    ```                           NOTE  ```
    ```    ```
    ```    ```
    ```  PGM: C:\Tut\Tut_GrfTwoWthTtl.sas  ```
    ```  OUT: C:\Tut\Tut_GrfTwoWthTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```    ```
    ```    ```
    ```    ```
    ```  WANT (Text from images)  ```
    ```  =======================  ```
    ```    ```
    ```  MYSTUDY C304456 AJAX  ```
    ```  DRAFT VER 1.0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```  NOTE2  ```
    ```  NOTE3  ```
    ```  NOTE  ```
    ```    ```
    ```    ```
    ```  PGM: C:\Tut\Tut_GrfTwoWthTtl.sas  ```
    ```  OUT: C:\Tut\Tut_GrfTwoWthTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```    ```
    ```  *                _           _  ```
    ```   _ __ ___   __ _| | _____   (_)_ __ ___   __ _  __ _  ___  ___  ```
    ```  | '_ ` _ \ / _` | |/ / _ \  | | '_ ` _ \ / _` |/ _` |/ _ \/ __|  ```
    ```  | | | | | | (_| |   <  __/  | | | | | | | (_| | (_| |  __/\__ \  ```
    ```  |_| |_| |_|\__,_|_|\_\___|  |_|_| |_| |_|\__,_|\__, |\___||___/  ```
    ```                                                 |___/  ```
    ```  ;  ```
    ```    ```
    ```  %macro tesser(device=png300,type=png);  ```
    ```    ```
    ```   filename outfile "d:\tesser\&type..&type";  ```
    ```   goptions  ```
    ```      reset=all  ```
    ```      rotate=portrait  ```
    ```      gsfmode = replace  ```
    ```      device  = &device  ```
    ```      gsfname = outfile  ```
    ```      vsize=10in  ```
    ```      hsize=8in  ```
    ```      htext=2 ;  ```
    ```    run;quit;  ```
    ```    ```
    ```    proc gslide ;  ```
    ```    ```
    ```     title1 j=l h=2 font='Simplex' "MYSTUDY C04456" j=r "AJAX";  ```
    ```     title2 j=l h=2 font='Couier' "DRAFT" j=r "VER 1.0";  ```
    ```     title3 j=l h=2 " ";  ```
    ```     title4 j=c h=3.0 font='Helvetica' "Ajax Study";  ```
    ```     title5 j=c h=3.0 font='Arial' "Dose and Placebo";  ```
    ```     note j=c h=5 "NOTE1";  ```
    ```     note j=c h=5 "NOTE2";  ```
    ```     note j=c h=5 "NOTE3";  ```
    ```     note j=c h=5 "NOTE";  ```
    ```     footnote1 j=l h=2 font='Times Roman' "PGM: C:\Tut\Tut_GrfTwoWthTtl.sas ";  ```
    ```     footnote2 j=l h=2 font='Helvetica'   "OUT: C:\Tut\Tut_GrfTwoWthTtl.pdf - &sysdate &systime";  ```
    ```    ```
    ```    run;  ```
    ```    quit;  ```
    ```    ```
    ```    goptions reset=all;  ```
    ```    filename outfile clear;  ```
    ```    run;quit;  ```
    ```    ```
    ```    * convert to text;  ```
    ```    x c:/progra~2/tesseract-ocr/tesseract d:/tesser/&type..&type d:/tesser/&type..txt;  ```
    ```    ```
    ```  %mend tesser;  ```
    ```    ```
    ```    ```
    ```  *          _       _   _  ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __  ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \  ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |  ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|  ```
    ```    ```
    ```  ;  ```
    ```    ```
    ```  %tesser(device=png300,type=png);  ```
    ```  %tesser(device=jpeg300,type=jpg);  ```
    ```  %tesser(device=bmp,type=bmp);  ```
    ```  %tesser(device=tiff,type=tiff);  ```
    ```  %tesser(device=gif,type=gif);  ```
    ```    ```
    ```  * Here is how to handle a PDF;  ```
    ```    ```
    ```  Note pdf's often contain embedded fonts so it is better to use another tool to extract the text.  ```
    ```  There are many free tools acrobat(even reader?), pdfwriter and pdf2text, boxoft and others in R nd Python.  ```
    ```    ```
    ```  You can convert the pdf to an image using free goshtscript at http://www.ghostscript.com/download/gsdnld.html.  ```
    ```  You really only need  gswin64.exe.  ```
    ```    ```
    ```  Converting a pdf to a tiff and ectracting the text using tesseract,  ```
    ```    ```
    ```  x C:\Progra~1\gs\gs9.19\bin\gswin64.exe -dNOPAUSE -dBATCH -sDEVICE=tiffg4 -sOutputFile=d:/tesser/pdftif.tiff d:/tesser/pdf.pdf;  ```
    ```  x c:/progra~2/tesseract-ocr/tesseract d:/tesser/pdftif.tiff d:/tesser/pdftif.txt;  ```
    ```    ```
    ```    ```
    ```  TEXT files I created (not perfect and each may be a little different  ```
    ```    ```
    ```    ```
    ```  *                               _                    _               _  ```
    ```    _____  ____ _ _ __ ___  _ __ | | ___    ___  _   _| |_ _ __  _   _| |_  ```
    ```   / _ \ \/ / _` | '_ ` _ \| '_ \| |/ _ \  / _ \| | | | __| '_ \| | | | __|  ```
    ```  |  __/>  < (_| | | | | | | |_) | |  __/ | (_) | |_| | |_| |_) | |_| | |_  ```
    ```   \___/_/\_\__,_|_| |_| |_| .__/|_|\___|  \___/ \__,_|\__| .__/ \__,_|\__|  ```
    ```                           |_|                            |_|  ```
    ```  ;  ```
    ```    ```
    ```    ```
    ```  /*  ```
    ```    ```
    ```  ****   *   *   ***  ```
    ```  *   *  **  *  *   *  ```
    ```  *   *  * * *  *  ```
    ```  ****   *  **  * ***  ```
    ```  *      *   *  *   *  ```
    ```  *      *   *  *   *  ```
    ```  *      *   *   ***  ```
    ```    ```
    ```  #! PNG ;  ```
    ```    ```
    ```    ```
    ```  d:/tesser/png.txt  ```
    ```    ```
    ```  MYSTU DY CO4456 AJAX  ```
    ```  DRAFT VER 1 .0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```  NOTEZ  ```
    ```  NOTES  ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\| ut\l 961wÂ§ththas  ```
    ```    ```
    ```  OUT: C:\Tut\Tut_GrF|'wo_VVthTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```      *  ****    ***  ```
    ```      *  *   *  *   *  ```
    ```      *  *   *  *  ```
    ```      *  ****   * ***  ```
    ```      *  *      *   *  ```
    ```  *   *  *      *   *  ```
    ```   ***   *       ***  ```
    ```    ```
    ```  #! JPG ;  ```
    ```    ```
    ```    ```
    ```  MYSTUDY CO4456 AJAX  ```
    ```  DRAFT VER 1.0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```    ```
    ```  NOTEZ  ```
    ```    ```
    ```  NOTE3  ```
    ```    ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\Tut\Tut_GrfTwthhTtl.sas  ```
    ```  OUT: C:\Tut\Tut_GrfTwthhTtl.pdf - 16AUG16 06:21  ```
    ```  MYSTUDY (304456 AJAX  ```
    ```  DRAFT VER 1.0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```  NOTEZ  ```
    ```  NOTES  ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\| ut\l 961wÂ§ththas  ```
    ```    ```
    ```  OUT: C:\Tut\Tut_GrF|'wo_VVthTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```    ```
    ```  ****   ****   *****  *****  *****  *****  ```
    ```  *   *   *  *  *        *      *    *  ```
    ```  *   *   *  *  *        *      *    *  ```
    ```  ****    *  *  ****     *      *    ****  ```
    ```  *       *  *  *        *      *    *  ```
    ```  *       *  *  *        *      *    *  ```
    ```  *      ****   *        *    *****  *  ```
    ```    ```
    ```    ```
    ```  MYSTUDY CO4456 AJAX  ```
    ```  DRAFT VER 1.0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```    ```
    ```  NOTE2  ```
    ```    ```
    ```  NOTE3  ```
    ```    ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\Tut\Tut_GrfTwthhTtl.sas  ```
    ```  OUT: C:\Tut\Tut_GrfTwthhTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```  ****   *   *  ****  ```
    ```   *  *  ** **  *   *  ```
    ```   *  *  * * *  *   *  ```
    ```   ***   *   *  ****  ```
    ```   *  *  *   *  *  ```
    ```   *  *  *   *  *  ```
    ```  ****   *   *  *  ```
    ```    ```
    ```  #! BMP ;  ```
    ```    ```
    ```  MYSTUDY CO4456 AJAX  ```
    ```  DRAFT VER 1.0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```    ```
    ```  NOTEZ  ```
    ```    ```
    ```  NOTE3  ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\Tut\Tut_GrfTwthhTtl.sas  ```
    ```  OUT: C:\Tut\Tut_GrfTwthhTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```  *****  *****  *****  *****  ```
    ```    *      *    *      *  ```
    ```    *      *    *      *  ```
    ```    *      *    ****   ****  ```
    ```    *      *    *      *  ```
    ```    *      *    *      *  ```
    ```    *    *****  *      *  ```
    ```    ```
    ```  #! TIFF ;  ```
    ```    ```
    ```  MYSTUDY (304456 AJAX  ```
    ```  DRAFT VER 1.0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```  NOTEZ  ```
    ```  NOTES  ```
    ```    ```
    ```  PGM: C:\| ut\l 961wÂ§ththas  ```
    ```    ```
    ```  OUT: C:\Tut\Tut_GrF|'wo_VVthTtl.pdf - 16AUG16 06:21  ```
    ```    ```
    ```   ***   *****  *****  ```
    ```  *   *    *    *  ```
    ```  *        *    *  ```
    ```  * ***    *    ****  ```
    ```  *   *    *    *  ```
    ```  *   *    *    *  ```
    ```   ***   *****  *  ```
    ```    ```
    ```  #! GIF ;  ```
    ```    ```
    ```    ```
    ```  MYSTU DY CO4456 AJAX  ```
    ```  DRAFT VER 1 .0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```    ```
    ```  NOTE2  ```
    ```    ```
    ```  NOTE3  ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\Tut\Tut_Gnâ€˜TwthhTt|.sas  ```
    ```  OUT: C:\Tut\Tut_Gnâ€˜TwthhTt|.pdf - 16AUG16 06:21  ```
    ```  MYSTU DY CO4456 AJAX  ```
    ```  DRAFT VER 1 .0  ```
    ```    ```
    ```  Ajax Study  ```
    ```  Dose and Placebo  ```
    ```    ```
    ```  NOTE1  ```
    ```    ```
    ```  NOTE2  ```
    ```    ```
    ```  NOTE3  ```
    ```  NOTE  ```
    ```    ```
    ```  PGM: C:\Tut\Tut_Gnâ€˜TwthhTt|.sas  ```
    ```  OUT: C:\Tut\Tut_Gnâ€˜TwthhTt|.pdf - 16AUG16 06:21  ```
    ```    ```
    ```    ```
