Link: https://ctf.viblo.asia/puzzles/sun-service-knjw1vcjylx
Truy cập tới http://172.104.49.143:1317/, ta thấy một ping service
<img width="1010" height="307" alt="image" src="https://github.com/user-attachments/assets/c040452a-be36-4eed-983a-ffdb0dd60fcf" />
Thường với bài như này thì sẽ về OS commmand injection thôi
<img width="1029" height="345" alt="image" src="https://github.com/user-attachments/assets/135d6bc0-1dac-48a8-986a-d88fc3a1d091" />
=> Chạy command ```google.com;ls```ta thấy file index.php => OS command injection thật.
khi cố đọc file index.php bằng ```google.com;cat index.php``` thì nhận được response "Th1nk mor3 s1mpl3!"
<img width="529" height="168" alt="image" src="https://github.com/user-attachments/assets/51d201e0-dcf9-47f5-a946-d5be6bc47b4e" />

Thử với nhiều payload khác đều bị vậy, có khả năng nó chặn cái gì đó =)) cũng phải thôi, bài 200đ thì cũng phải có thêm phần sau nữa chứ. Tìm trên google cách bypass 
<img width="1691" height="808" alt="image" src="https://github.com/user-attachments/assets/615f5a4d-23f9-4d3d-8cae-83fbfd195e6d" />
Và kết quả là đã đọc file thành công với command ```google.com;cat${IFS}index.php```
<img width="1303" height="638" alt="image" src="https://github.com/user-attachments/assets/c0fb782a-4b58-4a68-b453-b7656011518d" />
View page source, ta thấy được code và flag
<img width="1053" height="553" alt="image" src="https://github.com/user-attachments/assets/1f335047-695c-4580-a366-380df50d0557" />
=> Flag{Th1s_1s_4n_3asY_FL4G_R1ght?}




