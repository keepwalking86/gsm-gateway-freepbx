# Asterisk FreePBX System

# Tables of contents

- [1. Về Asterisk](#about-asterisk)
- [2. FreePBX Distro](#freepbx-distro)
- [3. Về mô hình kết nối GSM Gateway và FreePBX](#about-gsmgateway-freepbx)

## <a name="about-asterisk">1. Về Asterisk</a>

Asterisk là phần mềm dùng làm tổng đài điện thoại - Private Branch Excahnge (PBX). Kết hợp với các giao diện phần cứng điện thoại phù hợp và các ứng dụng mạng, Asterisk được sử dụng để thiết lập và kiểm soát các cuộc gọi giữa các điểm cuối viễn thông, cho phép thực hiện các cuộc gọi nội bộ với nhau, hoặc kết nối với với hệ thống mạng điện thoại chuyển mạch công cộng - Public switched telephone network (PSTN) và các thiết bị hoặc dịch vụ thoại qua mạng IP (VoIP).

Asterisk hỗ trợ nhiều chuẩn giao thức của VoIP như SIP và H.323, MGCP. Nó có thể hoạt động như trạm kết nối giữa các IP phone và mạng PSTN qua giao diện T- hoặc E-carrier hoặc card analog FXO.

Asterisk ra đời vào năm 1999 bởi Mark Spencer, hiện nay thì nó được phát triển bởi Sangoma Technologies Corporation.

Asterisk là phần mềm nguồn mở và nó có thể chạy trên nhiều nền tảng OS như Linux, BSD, MacOS, ..

Mô hình giải pháp tổng đài Asterisk

<p align="center">
<img src="../images/asterisk.jpg" />
</p>

Một số tính năng chính của Asterisk:

- Voicemail: Tính năng cho phép thực hiện thư thoại. Khi điện thoại bận thì asterisk định hướng cuộc gọi đến hộp thư thoại tương ứng đã khai báo trước

- IVR (Interactive Voice Response): Được dùng để chỉ chức năng tương tác thoại (tổng đài trả lời tự động).

- Conference calling: Tính năng cho phép cuộc gọi đàm thoại giữa nhiều người, và có thể thiết lập người nhận cuộc gọi chỉ có thể nghe và không có thể nói.

- Automated Call Distribution: Hệ thống sẽ tự động phân phối cuộc gọi phù hợp với tương tác của người dùng đối với hệ thống.

- Call Forwarding: Tính năng chuyển hướng cuộc gọi khi máy đang bận hoặc không trả lời


## <a name="freepbx-distro">2. FreePBX Distro</a>

Trước đây, việc xây dựng hệ thống tổng đài Asterisk được thực hiện thủ công với các bước sau:

- Dựng hệ điều hành phù hợp (Thường là linux như CentOS)

- Download, cài đặt và cấu hình Asterisk trên OS. Việc cấu hình Asterisk được thao tác trên từng tệp tin.

- Cài đặt và tích hợp gói DAHDI (Zaptel) để cho phép Asterisk giao tiếp với điện thoại analog hoặc hệ thống PSTN

...

Việc thao tác nhiều công việc thủ công như vậy chiếm rất nhiều thời gian và dễ xảy ra sai xót. Vì vậy mà hiện nay, nhiều bản distro ra đời mà tích hợp đầy đủ các thành phần của việc xây dựng hệ thống tổng đài như OS, Asterisk, Giao diện, DAHDI và nhiều gói hỗ trợ khác, giúp cho việc triển khai được nhanh chóng và chính xác hơn.

Một số bản distro Asterisk phổ biến hiện nay:

- Elastix – Debian Linux Asterisk Distribution

- PBXinaflash – Linux PBX

- FreePBX – Based on CENTOS – most module require payment

FreePBX Distro là bản OS dựa trên CentOS, gồm giao diện đồ họa (FreePBX) cho cấu hình và quản lý Assterisk. FreePBX Distro gồm các gói cài đặt mà cung cấp các tính năng như VoIP, PBX, Fax, IVR, Voicemail.

## <a name="about-gsmgateway-freepbx">3. Về mô hình kết nối GSM Gateway và FreePBX</a>

Với doanh nghiệp mà có bộ phận chăm sóc khách hàng đông, với nhu cầu thực hiện nhiều cuộc gọi, khi đó yêu cầu đặt ra là:

- Có thể sử dụng gọi nội bộ mà không mất chi phí

- Có thể thực hiện được cuộc gọi trên IP phone, mobile, PC qua mạng

- Tiết kiệm chi phí cuộc gọi ra ( nghĩa là gọi số của nhà mạng nào thì tự động định tuyến qua SIM của nhà mạng đó)

- Khi một người trong hệ thống bận hoặc không trả lời, người khác có thể thực hiện nhận cuộc gọi đó.

- Lưu trữ ghi âm cuộc gọi tập trung

...

Khi đó, mô hình hệ thống tổng đài IP (IP PBX) kết hợp GSM Gateway ra đời cho phép đáp ứng các yêu cầu trên.

<p align="center"> 
<img src="../images/gsm-freepbx.png" />
</p>

**GSM Gateway là gì?**

GSM Gateway là thiết bị mà dùng kết nối giữa tổng đài VoIP

GSM Gateway là thiết bị dùng để định tuyến trực tiếp giữa các mạng IP, digital, analog và GSM. Ý tưởng cốt lõi chính của GSM Gateway là tiết kiệm chi phí dựa trên giao thức định tuyến giá thấp nhất (Tiếng Anh là Least Cost Routing - LCR). Bởi vì các thẻ sim và các module GSM được tích hợp trong GSM Gateway, khi đó cuộc gọi sẽ được thực hiện từ GSM đến GSM, thay vì thực hiện từ IP đến GSM, vì vậy mà giá tiền cuộc gọi sẽ rẻ hơn. Ngoài ra, với giao thức LCR, cuộc gọi qua GSM Gateway sẽ được kết nối đến cùng nhà mạng với người nhận cuộc gọi (ví dụ Viettel gọi Viettel, Mobifone gọi Mobifone, ..) vì vậy mà chi phí sẽ thấp nhất.

**Các GSM Gateway thường có các tính năng như sau**:

- Cho phép kết nối với các tổng đài IP

- Sử dụng với các nhà mạng như Viettel, Mobifone, Vinaphone, Gphone...

- Tự động định tuyến số điện thoại gọi ra theo nhà mạng (nghĩa là gọi số của nhà mạng nào thì tự động định tuyến qua SIM của nhà mạng đó)

- Cho phép giới hạn thời gian mỗi cuộc gọi, thời gan của mỗi sim

- Hiển thị trạng thái cuộc gọi đi, đến

Ngoài ra, một số GSM còn hỗ trợ API cho phép kết nối từ các phần mềm cho thông tin về các cuộc gọi, như sử dụng cho CRM, …
