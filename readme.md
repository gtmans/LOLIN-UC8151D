How2 make graphicsfile for LOLIN 8151D 121x104 on Windows PC

First download or create 2 .bmp images 121x104 pixels black (use Photoshop or MS Paint, You can use paint to save a picture as bmp 1 color)
Download and install a small utility called Image2Lcd at http://electronoobs.com/images/Arduino/tut_57/image2LCD.zip
use sample LOLIN EPD sketch (file/examples in Arduino EPD) "test_2_13inch_212x104_TRI-COLOR" and change image.h tab

- start Image2Lcd
- open image
- select C array, Vertical scan, monochrome, 212x104
- select include head data, Scan Right to Left and Scan Bottom to top
- select reverse color and mirror up down
- save file

![how2](https://github.com/gtmans/LOLIN-UC8151D/blob/main/howto_LOLINUC8151D_image.png)

- copy all from the outputfile to the first half of image.h part (over existing "const unsigned char gImage_black[2756] upto ,}; stop end before the second const unsigned char gImage_red[2756] *)
- remove the first 6 bytes or put them inbetween /* and */ or put them on the second line and // them out
- reduce the length of the array in the first line with 6: [2762-6] or [2756]
- the number of bytes for the whole screen is (212x104)/8bits=2756
- copy the name of the "const unsigned char" and paste it in "test_2_13inch_212x104_TRI-COLOR" on 
line 30 over "gImage_black"

*) easier is to copy all lines exept the first line and paste them at line 2 to line 175. Then you don't have to change the length or name gImage_black

![testprogram](https://github.com/gtmans/LOLIN-UC8151D/blob/main/testprogram.png)

-convert the second (red) image the same way
-remove the first 6 bytes or put them on the second line and // them out
-reduce the length of the array in the first line with 6: [2762-6] or [2756]
-copy all from the outputfile to the second half of image.h part (over existing "const unsigned char gImage_red[2756] upto the end
-copy the name of the "const unsigned char" and paste it in "test_2_13inch_212x104_TRI-COLOR" on 
line 30 over "gImage_red"

![LOLIN-setup](https://github.com/gtmans/LOLIN-UC8151D/blob/main/LOLIN-setup.png)

