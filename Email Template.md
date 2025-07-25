link: https://ctf.viblo.asia/puzzles/email-template-6xgpvznenzc

Truy cập http://172.104.49.143:1609/ và login với user: user1/user1
<img width="1770" height="603" alt="image" src="https://github.com/user-attachments/assets/ffe31fa4-1604-4923-b059-59a959e45877" />

Nhưng user này không có quyền truy cập tính năng "Edit template"
<img width="1186" height="348" alt="image" src="https://github.com/user-attachments/assets/1c1b30c1-155f-4a17-9120-309f4a12895d" />
Thử đi scan port bằng nmap và file ẩn cũng không có gì, ta quay lại phần token đáng nghi hiển thị ở profile của user

Dùng Jwt tool để crack jwt token, ta thấy nó sử dụng secret key là "secret"
<img width="1453" height="314" alt="image" src="https://github.com/user-attachments/assets/1be2acb5-8d83-41a2-85fd-0bf628f7762a" />
Sử dụng secret này để tạo jwt token của admin
<img width="1259" height="667" alt="image" src="https://github.com/user-attachments/assets/e653bbb1-b3bf-4c6e-9928-33bf1148f421" />
Sử dụng token này, ta thành công truy cập tài khoản admin
<img width="1764" height="789" alt="image" src="https://github.com/user-attachments/assets/2988778c-acbc-497a-9a0b-a5fc31cf93cd" />
Với User admin này, ta đã có thể truy cập được chức năng "Edit template"
<img width="1846" height="815" alt="image" src="https://github.com/user-attachments/assets/d9684b09-d41b-466c-a1d2-c55acfcd0402" />
Test thử với payload "{{7*7}}" ta thấy response trả về là 49. => Lỗi SSTI với ngôn ngữ python
<img width="1920" height="513" alt="image" src="https://github.com/user-attachments/assets/f9e9cdd6-99f8-46aa-a635-2264dc005486" />
Sử dụng payload ```{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls%20-a').read()}}``` để đọc file
<img width="1438" height="592" alt="image" src="https://github.com/user-attachments/assets/d15e6635-c090-4d73-8448-4763e9a80556" />
Dùng payload ```{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen('cat%20flag.py').read()}}``` tìm được flag.
<img width="1434" height="784" alt="image" src="https://github.com/user-attachments/assets/8f0de944-0cba-488c-ad60-9a611f49f255" />

=> Flag{viBlo_CtF_2024_ssTI}


