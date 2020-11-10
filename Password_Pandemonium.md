# Password Pandemonium
You're looking to book a flight to Florida with the totally-legit new budget airline, Oceanic Airlines! All you need to do is create an account! Should be pretty easy, right?

...right?    
https://pandemonium.web.2020.sunshinectf.org 
![alt text](https://github.com/kietpham0703/Writeup_BOOTCAMP_CTF/blob/main/Screen%20Shot%202020-11-10%20at%202.20.55%20AM.png)  
CÁCH GIẢI:   
Thử tạo tài khoản Username: admin Password: 12345678 báo lỗi:   
1.Error! Password must include at least one letter.(mật khẩu phải bao gồm ít nhất 1 chữ)  
  
Username: admin Password: abc123456 báo lỗi:   
2.Error! Password must include more than two special characters.(mật khẩu phải bao gồm nhiều hơn hai ký tự đặc biệt) 
  
Username: admin Password: ""abc123456"" báo lỗi:  
3.Error! Password must include a prime amount of numbers.(mật khẩu bao gồm 1 số nguyên tố các chữ số 2,3,5,7.....)  
  
Username: admin Password: "abc3"3abc" báo lỗi:  
4.Error! Password must have equal amount of uppercase and lowercase characters.(mật khẩu phải có số lượng ký tự viết hoa và viết thường bằng nhau Vd:Aa,Bb,Cc...)  
  
Username: admin Password: "Aa3"3Aa" báo lỗi:  
5.Error! Password must include an emoji.(mật khẩu phải bao gồm một biểu tượng cảm xúc)  
  
Username: admin Password: "😁Aa3"3Aa" báo lỗi:  
6.Error! Password's MD5 hash must start with a number.(Hàm băm MD5 của mật khẩu phải bắt đầu bằng một số, dùng www.md5online.org ta sẽ kiểm tra được mật khẩu mình đặt có hàm băm MD5 bắt đầu bằng 1 số hay không VD "aA3"😁aA3"= 6c5b...)  
  
Username: admin Password: "aA3"😁aA3" báo lỗi:  
7.Error! Password must be valid JavaScript that evaluates to True.(Mật khẩu phải là code JavaScript giá trị trả về là True ta có thể dùng console trong DevelopTool để check "aA😁3"=="aA😁3"= 0afa...)  
![alt text](https://github.com/kietpham0703/Writeup_BOOTCAMP_CTF/blob/main/Screen%20Shot%202020-11-10%20at%201.46.06%20AM.png)  
  
Username: admin Password: "aA😁3"=="aA😁3" báo lỗi:  
8.Error! Password must be a palindrome.(mật khẩu đối xứng viết xuôi hay viết ngược vẫn chỉ cho ra một VD Aa=aA, 123321,... Ở đây nếu như đối xứng "aA😁3"=="3😁Aa" thì code Javascript sẽ không còn trả về true nữa. Vì vậy, thay vì cho 2 cái bằng nhau thì ta cho chúng khác nhau để trả giá trị về True nhưng để đáp ứng yêu cầu đối xứng thì phải dùng là !=!. Trong trường hợp này thì JavaScript != và !=! giống nhau vì nó chỉ xét dấu khác sau đó thì dấu chấm than phía sau sẽ bị bỏ qua nên ta được "aA😁3"!=!"3😁Aa" =56b3... thoả điều kiện)    
![alt text](https://github.com/kietpham0703/Writeup_BOOTCAMP_CTF/blob/main/Screen%20Shot%202020-11-10%20at%202.14.23%20AM.png)  
Username: admin Password: "aA😁3"!=!"3😁Aa":  
![alt text](https://github.com/kietpham0703/Writeup_BOOTCAMP_CTF/blob/main/Screen%20Shot%202020-11-10%20at%202.16.37%20AM.png)  
flag: sun{Pal1ndr0m1c_EcMaScRiPt}
