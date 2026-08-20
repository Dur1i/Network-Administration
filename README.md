# 🖥️ Quản Trị Mạng - Triển Khai Mạng Doanh Nghiệp Nhỏ (SME)

## 📖 Giới thiệu tổng quan
Dự án này là đồ án môn học **Quản trị Mạng (Network Administration)**, tập trung vào việc thiết kế và cấu hình toàn diện hạ tầng mạng và máy chủ cho một doanh nghiệp vừa và nhỏ (SME - Small and Medium-sized Enterprises).

Dựa trên kịch bản thực tế của công ty "Emgroup" (hoạt động trong lĩnh vực Bất động sản), nhóm đã xây dựng hệ thống mạng cục bộ, triển khai các dịch vụ máy chủ cốt lõi trên nền tảng **Windows Server** và định tuyến/bảo mật thông qua **pfSense**.

**Thành viên thực hiện:**
- Ngô Quốc Cường
- Lương Hoàng Thông
- Bùi Trung Kiên

## 🎯 Mục tiêu dự án
- Thiết kế sơ đồ mạng vật lý và logic phân vùng an toàn cho các phòng ban (Kế toán, Lập trình, Ban giám đốc/Admin).
- Tự động hóa cấp phát IP và phân giải tên miền.
- Quản lý tài nguyên, người dùng và phân quyền tập trung bằng Domain Controller.
- Cung cấp các dịch vụ nội bộ quan trọng: Web, Mail, File Sharing.
- Đảm bảo tính sẵn sàng cao, dự phòng dữ liệu và phục hồi khi có sự cố.

## 🛠️ Công nghệ & Giải pháp triển khai
Dự án áp dụng các công nghệ tiêu chuẩn của Microsoft và mã nguồn mở:
- **Windows Server:** Hệ điều hành máy chủ chính triển khai các Role quan trọng.
- **Active Directory Domain Services (AD DS):** Quản lý tập trung tài khoản, nhóm (OU) và áp dụng Group Policy.
- **DNS & DHCP Server:** Cấp phát IP tự động và phân giải tên miền (sử dụng thêm DHCP Relay Agent).
- **IIS (Internet Information Services):** Triển khai Web Server nội bộ (có tích hợp chứng chỉ số SSL/TLS để chạy HTTPS).
- **MDaemon Mail Server:** Hệ thống máy chủ Email để nhân viên liên lạc nội bộ.
- **File Server (DFS & Quota):** Quản lý lưu trữ tệp tin tập trung, phân quyền truy cập nghiêm ngặt và giới hạn dung lượng lưu trữ (Quota). Sử dụng Distributed File System (DFS) để đồng bộ dữ liệu.
- **Windows Server Backup:** Lên lịch sao lưu tự động và khôi phục dữ liệu (Disaster Recovery).

## 🚀 Các bước cấu hình & Thực nghiệm (Demo)
Nhóm đã giả lập hoàn chỉnh môi trường doanh nghiệp trên VMware và cấu hình thành công các hạng mục:
1. Nâng cấp Windows Server thành **Domain Controller** (DC) và đưa các máy Client (Windows 10) gia nhập (Join) Domain.
2. Cấu hình **DHCP Server** và **DHCP Relay Agent** để cấp IP khác dải (VLANs).
3. Triển khai **Web Server (HTTPS)** với chứng chỉ số tự cấp phát (CA), hỗ trợ truy cập an toàn.
4. Cấu hình **Mail Server MDaemon**, cho phép gửi/nhận email qua giao diện Webmail.
5. Cấu hình **File Server**:
   - Tạo thư mục chia sẻ theo phòng ban (Group Policy).
   - Thiết lập **Quota** (Hạn mức dung lượng) để chặn nhân viên lưu trữ quá mức quy định hoặc lưu file rác (Video, hình ảnh cá nhân).
   - Thiết lập **DFS Replication** để đồng bộ dữ liệu giữa các Server.
6. Lên lịch sao lưu (Backup) tự động và thử nghiệm khôi phục thành công tệp tin bị xóa.

***

*Đồ án đóng vai trò như một cẩm nang triển khai mạng toàn diện, giúp sinh viên nắm vững kỹ năng của một System/Network Administrator thực thụ trong môi trường doanh nghiệp Windows.*
