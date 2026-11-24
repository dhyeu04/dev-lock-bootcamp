# Session 06 - DApps & Web3 Ecosystem

- Student: Đỗ Duy Hiếu
- GitHub: https://github.com/dhyeu04
- Submitted: 24/11/2026
- **Commit:** `[S06] add devlog`

## 1. Summary

Buổi học giới thiệu dApp (ứng dụng phi tập trung) hoạt động như thế nào: giao diện người dùng nói chuyện với smart contract trên blockchain qua ví, các nhóm ứng dụng phổ biến trong Web3, vai trò của Oracle, và một mini demo chạy trên testnet.

## 2. Topic notes

### dApp Architecture

- dApp gồm hai phần: **frontend** (web/app như bình thường) và **smart contract** trên blockchain đóng vai trò backend.
- Điểm khác với app truyền thống: không có một server duy nhất nắm quyền kiểm soát dữ liệu và logic. Code contract và lịch sử giao dịch đều công khai, ai cũng kiểm tra được.
- Chi phí lưu trữ trên chuỗi đắt, nên file lớn (ảnh, video, tài liệu) thường để ở nơi khác như IPFS; trên chuỗi chỉ giữ hash hoặc đường dẫn tham chiếu.

### Luồng Frontend → Wallet → Smart Contract → Blockchain

1. **Frontend:** người dùng bấm một thao tác (ví dụ "Swap", "Mint").
2. **Wallet:** ví hiện chi tiết giao dịch, người dùng xem và **ký bằng private key**. Private key nằm ở ví của người dùng, dApp không nhìn thấy.
3. **Smart contract:** giao dịch đã ký được gửi đi và kích hoạt hàm tương ứng của contract.
4. **Blockchain:** các node kiểm tra, đưa giao dịch vào block và cập nhật trạng thái. Frontend đọc lại trạng thái mới để hiển thị kết quả.

### Các nhóm ứng dụng trong Web3

| Nhóm | Ý chính |
|---|---|
| DeFi | Dịch vụ tài chính (đổi token, cho vay, staking) chạy bằng smart contract, không qua ngân hàng/trung gian |
| Payment | Chuyển giá trị nhanh, xuyên biên giới, hay dùng stablecoin để tránh biến động giá |
| NFT | Token đại diện cho quyền sở hữu một tài sản số độc nhất (tranh, vé, vật phẩm) |
| Gaming | Vật phẩm trong game thuộc về người chơi và có thể chuyển nhượng/trao đổi |
| DAO | Tổ chức vận hành bằng luật ghi trong smart contract, thành viên bỏ phiếu để ra quyết định |

### Oracle (mức giới thiệu)

- Smart contract chỉ nhìn thấy dữ liệu bên trong blockchain, không tự lấy được giá, thời tiết hay kết quả sự kiện bên ngoài.
- **Oracle** là cầu nối đưa dữ liệu ngoài chuỗi vào contract. Nếu oracle cung cấp dữ liệu sai thì contract vẫn chạy đúng code nhưng cho ra kết quả sai, nên độ tin cậy của oracle rất quan trọng.

### Mini demo trên Testnet

- Testnet là mạng thử nghiệm, token ở đó không có giá trị thật nên có thể thử giao dịch mà không sợ mất tiền.
- Các bước: kết nối ví với dApp → thực hiện một thao tác → ký giao dịch trong ví → theo dõi kết quả trên block explorer.

## 3. Work completed



## 4. Evidence

https://canva.link/bqe48vrodrubm04

## 5. Blockers



## 6. Takeaway

Điểm khác biệt lớn nhất của dApp là logic nằm trong contract công khai và người dùng tự giữ khóa qua ví. Vì vậy trước khi bấm ký bất kỳ giao dịch nào, mình cần đọc kỹ xem giao dịch đó sẽ làm gì.
