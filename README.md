# SQ-data-cleaning
## upload data club_member
Đây là dự án đầu tiên của tôi sử dụng SQL để làm sạch dữ liệu

## Upload data club member lên dveaver

## Mô tả đữ liệu

|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|

## xóa khoảng trắng đầu và cuối, sử dụng TRIM
    UPDATE club_member_info_clean  SET full_name = TRIM(full_name)
## đổi định dạng của cột full_name
- upper chữ cái đầu tiên
  
    SELECT UPPER(SUBSTRING(full_name, 1,1)), full_name FROM club_member_info_clean
  
- nối kí tự đầu vào phần còn lại của chuỗi
  
    UPDATE club_member_info_clean
    SET full_name = CONCAT(UPPER(SUBSTRING(full_name, 1,1)), SUBSTRING(full_name,2, 99)
  
- C2: select concat(UPPER(SUBSTRING(full_name, 1,1)), SUBSTRING(full_name, 2,LENGHT(full_name)-1) full_name_adj, full_name FROM club_member_info_clean
  
## chỉnh sửa lại tuổi ngoài phạm vi thực tế
- tìm những hàng bị trống dữ liệu và thay bằng 45 tuổi
  
    UPDATE club_member_info_clean SET age = 45 WHERE age = ''

- tìm những giá trị tuổi phi thực tế
  
    SELECT MAX(age) FROM club_member_info_clean WHERE age > 80
  
- thay những giá trị đã tìm được thành tuổi trung bình
  
    UPDATE club_member_info_clean SET age = 45 WHERE age >80
    

