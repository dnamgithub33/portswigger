[API testing](#api-testing)

# API testing

1. API recon

    Để bắt đầu API testing, cần phải tìm hiểu thật kỹ về API đó, để khám phá các bề mặt tấn công của nó.
    Để bắt đầu, cần xác định các API endpoint là những nơi mà API trả về các tài nguyên được yêu cầu.
2. API doc

    Để hiểu rõ nhất cách hoạt động, cách sử dụng API, cần sử dụng API Doc.

    Lab: Exploiting an API endpoint using documentation

    ![img](/API_testing_img/1.png)

    Để hoàn thành lab, cần tìm được API doc bị lộ và xóa ```carlos```.

    Ở phần lý thuyết, ta được biết API doc đôi khi có thể bị lộ ở một số đường dẫn như sau:

    ![img](/API_testing_img/2.png)

    Tiến hành thử với đường dẫn ```/api``` ta thu được API doc bị lộ như sau:

    ![img](/API_testing_img/3.png)

    Trong đó ta thấy có một API có method DELETE có chức năng xóa user như sau, nó cho phép xóa user với đường dẫn ```/user/[string]``` với string ở đây là tên của người cần xóa:

    ![img](/API_testing_img/4.png)

    Ta có thể send request ngay để hoàn thiện bài lab nhưng ở đây ra sẽ không làm thế.
    Tiến hành chạy lệnh curl mà API doc cung cấp để xóa ```carlos```:

    ![img](/API_testing_img/5.png)

    Nhưng hệ thống lại báo lỗi ```Unauthorized```

    ![img](/API_testing_img/6.png)

    Tiên thành thêm cookie, câu lệnh sẽ thành như sau:

    ```
    curl -vgw "\n" -X DELETE 'https://0a51009703ec760f8088a398008900ca.web-security-academy.net/api/user/carlos' -d '{}' -b 'session=Du2koBQh1Dgk4gVy2szvPTRZCGjSMfU3'
    ```

    Hoàn thiện xóa user và giải được lab:

    ![img](/API_testing_img/7.png)

    ![img](/API_testing_img/8.png)

    Việc dò các API doc bị lộ này có thể dùng tool như ```Burp Scanner``` để rà quét.

3. Lab: Finding and exploiting an unused API endpoint

    Để hoàn thành bài lab ta cần hoàn mua được sản phẩm Lightweight l33t Leather Jacket. Nhưng hoàn toàn không đủ số dư.

    ![img](/API_testing_img/9.png)

    Trong HTTP History, có một request lấy thông tin sản phẩm như sau:

    ![img](/API_testing_img/10.png)

    Thử dùng Method OPTIONS để xem các method cho phép đến API này:

    ![img](/API_testing_img/11.png)
    
    Trong đó method ```PATCH``` cho phép cập nhật một phần tài nguyên. Tiến hành chỉnh sửa giá của sản phẩm để mua được:

    ![img](/API_testing_img/12.png)

    Và rồi có thể mua được sản phẩm:

    ![img](/API_testing_img/13.png)











4. Lab: Exploiting a mass assignment vulnerability

    Tương tự bài trước, bài này cần mua được sản phẩm Lightweight l33t Leather Jacket

    ![img](/API_testing_img/14.png)

    Ta có gói tin để lấy thông tin giỏ hàng như sau:

    ![img](/API_testing_img/15.png)

    và gói tin để thêm mặt hàng vào giỏ:

    ![img](/API_testing_img/16.png)

    Tiến hành ```POST``` JSON sản phẩm có mã giảm giá 100% vào giỏ hàng:

    ![img](/API_testing_img/17.png)




