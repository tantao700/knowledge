#ffmpeg video edit

- ffmpeg -i test.mov -b:v 2048k -s 1920x1080 ./test_zip.mp4

-i 输入文件的路径或者url；
-s 设置输出文件的分辨率,wxh；
-b:v 输出文件的码率，一般500k左右即可，人眼看不到明显的闪烁，这个是与视频大小最直接相关的
