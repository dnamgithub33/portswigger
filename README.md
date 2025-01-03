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


