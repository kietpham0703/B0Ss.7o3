# CRYPTO: Magically Delicious (SunshineCTF) 

Can you help me decipher this message?  
⭐🌈🍀 ⭐🌈🦄 ⭐🦄🌈 ⭐🎈🍀 ⭐🦄🌑 ⭐🌈🦄 ⭐🌑🍀 ⭐🦄🍀 ⭐🎈⭐ 🦄🦄 ⭐🦄🎈 ⭐🌑🍀 ⭐🌈🌑 ⭐🌑⭐ ⭐🦄🌑 🦄🦄 ⭐🌑🦄 ⭐🦄🌈 ⭐🌑🍀 ⭐🦄🎈 ⭐🌑🌑 ⭐🦄⭐ ⭐🦄🌈 ⭐🌑🎈 🦄🦄 ⭐🦄⭐ ⭐🌈🍀 🦄🦄 ⭐🌈🌑 ⭐🦄💜 ⭐🌑🦄 🦄🦄 ⭐🌑🐴 ⭐🌑🦄 ⭐🌈🍀 ⭐🌈🌑 🦄🦄 ⭐🌑🦄 ⭐🦄🌈 ⭐🌑🍀 ⭐🦄🎈 ⭐🌑🌑 ⭐🦄⭐ ⭐🦄🌈 ⭐🌑🎈 🦄🦄 ⭐🦄🦄 ⭐🌑🦄 ⭐🌈🌑 ⭐🦄💜 ⭐🦄🎈 ⭐🌑🌑 ⭐🎈🦄  
Note: If you don't see a message above, make sure your browser can render emojis.  
Tip: If you're digging into the unicode encoding of the emojis, you're on the wrong track!  
CÁCH GIẢI:   
Nhìn vào các kí tự trên ta sẽ nhận ra được 2 điểm đặc biệt của bài:  
I. Có tất cả 8 kí tự khác nhau: ⭐🌈🍀🦄🎈🌑🐴💜  
II. Có quy luật 3 emoji đứng chung với nhau   
=> Hệ Bát Phân (OCTAL)  
Dựa vào format của flag là sun{}. Chuyển sang hệ bát phân ta được  163 165 156 173 175  
Từ đó suy ra: ⭐=1 🌈=6 🍀=3 🦄=5 🎈=7 🌑=? 🐴=? 💜=?  
```py  
input="💜⭐🐴🍀🌑🦄🌈🎈" #Dự Đoán và thử thì ta được 💜=0 🐴=2 🌑=4
output="01234567"
x="⭐🌈🍀 ⭐🌈🦄 ⭐🦄🌈 ⭐🎈🍀 ⭐🦄🌑 ⭐🌈🦄 ⭐🌑🍀 ⭐🦄🍀 ⭐🎈⭐ 🦄🦄 ⭐🦄🎈 ⭐🌑🍀 ⭐🌈🌑 ⭐🌑⭐ ⭐🦄🌑 🦄🦄 ⭐🌑🦄 ⭐🦄🌈 ⭐🌑🍀 ⭐🦄🎈 ⭐🌑🌑 ⭐🦄⭐ ⭐🦄🌈 ⭐🌑🎈 🦄🦄 ⭐🦄⭐ ⭐🌈🍀 🦄🦄 ⭐🌈🌑 ⭐🦄💜 ⭐🌑🦄 🦄🦄 ⭐🌑🐴 ⭐🌑🦄 ⭐🌈🍀 ⭐🌈🌑 🦄🦄 ⭐🌑🦄 ⭐🦄🌈 ⭐🌑🍀 ⭐🦄🎈 ⭐🌑🌑 ⭐🦄⭐ ⭐🦄🌈 ⭐🌑🎈 🦄🦄 ⭐🦄🦄 ⭐🌑🦄 ⭐🌈🌑 ⭐🦄💜 ⭐🦄🎈 ⭐🌑🌑 ⭐🎈🦄"
trans = x.maketrans(input, output) 
def octal_to_str(octal_str):  #Hàm chuyển octal sang string
    str_converted = ""
    for octal_char in octal_str.split(" "):
        str_converted += chr(int(octal_char, 8))
    return str_converted
print(octal_to_str(x.translate(trans)))   
```
flag: sun{lucky-octal-encoding-is-the-best-encoding-method}   
