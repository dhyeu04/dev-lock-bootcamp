
# Session 02 - How Blockchain Works
- Student: Đỗ Duy Hiếu
- GitHub: https://github.com/dhyeu04
- Submitted: 2026-10-22
- Commit: https://github.com/dhyeu04/dev-lock-bootcamp

## 1. Summary
- **Block & Blockchain Structure**
Các block được liên kết với nhau thông qua mã hash của block trước đó
- **Transaction**
-Là đơn vị công việc nhỏ nhất làm thay đổi trạng thái của mạng lưới
    +Chuyển đổi giá trị
    +Thực thi logic 
    +Xác thực chữ ký
- **Ledger / State**
    -Ledger:Sổ cái lưu trữ mọi giao dịch(lịch sử biến động)
    -State: Trạng thái hiện tại( snapshot dữ liệu tại thời điểm hiện tại 
- **Nodes & P2P Network**
**P2P (Peer-to-Peer)** là mô hình Server-Server. 
Mỗi **Node** trong mạng lưới 
    +Đóng vai trò là client (nhận dữ liệu), 
    +Là server (cung cấp dữ liệu và xác thực)
**Full node**
    + Tải • xác minh • lưu lịch sử
    + Thực thi luật đồng thuận
**Light node**
    + Chỉ tải block header
    + Nhanh, nhẹ — phù hợp ví di động
- **Transaction Lifecycle**
<img width="857" height="353" alt="image" src="https://github.com/user-attachments/assets/83888fda-518b-48e4-975d-892bcc156c6f" />
- **Blockchain Explorer**(Trình khám phá blockchain)
Công cụ tìm kiếm trực tuyến cho phép bạn tra cứu, theo dõi và phân tích toàn bộ dữ liệu lịch sử cũng như các hoạt động đang diễn ra trên một mạng lưới blockchain
## 2. Topic notes
- **Block & Blockchain Structure**
  - 1 block
    + 1 mã hash chính nó
    + 1 mã hash của khối trước nó
    + thông tin
    + hình vẽ
      
      [khối N] - [Khối N+1]
      
      [Khối N+1] chứa mã hash chính nó và mã hash của khối N

   Note:
  
      1 khối block còn có phần head và body nữa ( liên quan tới light node)
  
      Đặc biệt khối block đầu sẽ không chứa mã hash của khối trước nó ( vì có đâu mà chứa)
  
  trước------[Khối]----sau
     
- **Transaction**
- **Ledger / State**
      tưởng tượng về tài khoản ngân hàng của bản thân cuối tháng
      +Lúc nhìn số dư còn 5.000VND ( thì đây là state)
      +Kiểm tra lại mình đã tiêu vào đâu mà chưa cuối tháng đã âm tiền vào lịch sử giao dịch kiểm tra ( đây là ledger)
- **Nodes & P2P Network**
- **Transaction Lifecycle**
- **Blockchain Explorer**
## 3. Work completed

## 4. Evidence

## 5. Blockers

## 6. Takeaway
