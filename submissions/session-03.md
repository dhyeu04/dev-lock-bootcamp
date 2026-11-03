# Session 03 - Cryptography & Wallet

- Student: Đỗ Duy Hiếu
- GitHub: https://github.com/dhyeu04
- Submitted: 3/11/2026
- Commit: https://github.com/dhyeu04/dev-lock-bootcamp

## 1. Summary

Buổi này đi qua nền tảng mật mã đứng sau blockchain: hàm băm (hashing), mã hóa đối xứng và bất đối xứng, cặp khóa public/private, chữ ký số, cách sinh địa chỉ ví, seed phrase, các loại ví (hot/cold, custodial/non-custodial) và những nguyên tắc cơ bản để giữ ví an toàn. Ý chính cần nhớ: ví không chứa coin, quyền kiểm soát tài sản nằm ở private key.

## 2. Topic notes

### 1. Hashing (hàm băm)

- Biến dữ liệu có độ dài bất kỳ thành một chuỗi có độ dài cố định (ví dụ SHA-256 luôn cho ra 256 bit). Có thể xem hash như "dấu vân tay" của dữ liệu.
- Đổi một ký tự ở đầu vào thì hash thay đổi hoàn toàn (ví dụ `Hello` và `HEllo` cho hai hash không liên quan gì nhau).

**Hash được dùng ở đâu trong blockchain**

1. Định danh giao dịch: mỗi transaction có một mã hash duy nhất.
2. Liên kết block: mỗi block lưu hash của block trước nên sửa một block sẽ làm hỏng cả chuỗi phía sau.
3. Merkle tree: gom hàng nghìn giao dịch về một hash duy nhất để dễ xác minh. Xây từ dưới lên, ví dụ 4 giao dịch → 4 hash → 2 hash → 1 hash gốc.
4. Proof of Work: đi tìm một hash thỏa điều kiện do mạng đặt ra.

**5 tính chất của hàm băm**

| Tính chất | Ý nghĩa |
|---|---|
| Một chiều | Gần như không thể suy ngược ra dữ liệu gốc từ hash |
| Xác định | Cùng đầu vào thì luôn ra cùng một đầu ra |
| Tính nhanh | Tính hash nhanh, không tốn nhiều tài nguyên |
| Hiệu ứng tuyết lở | Đầu vào chỉ lệch rất nhỏ cũng cho hash khác hoàn toàn |
| Kháng xung đột | Rất khó tìm hai đầu vào khác nhau mà cho cùng một hash |

### 2. Mã hóa

- Mã hóa một chiều: biến đổi dữ liệu mà không có đường quay lại (chính là hướng của hash).
- Mã hóa hai chiều: mã hóa được và giải mã ngược lại được, gồm hai loại dưới đây.

| | Đối xứng | Bất đối xứng |
|---|---|---|
| Khóa | Một khóa chung cho cả mã hóa và giải mã | Một cặp: public key và private key |
| Ví dụ | Mã Caesar: dịch mỗi ký tự đi k vị trí trong bảng chữ cái | Dùng public key của người nhận để khóa, chỉ private key của họ mới mở được |
| Rủi ro | Lộ khóa thì ai có khóa cũng giải mã được | Private key phải được giữ bí mật tuyệt đối |
| Vấn đề cần giải | Hai bên phải trao đổi khóa an toàn trước | Không cần chia sẻ bí mật trước, public key công khai được |

### 3. Public key và Private key

- Private key: một số ngẫu nhiên 256-bit, quyết định quyền sở hữu tài sản, phải giữ bí mật tuyệt đối.
- Public key: được tính ra từ private key bằng đường cong elliptic secp256k1, có thể chia sẻ công khai.
- Quy tắc một chiều: private key → public key thì dễ, ngược lại gần như không thể.

### 4. Chữ ký số (Digital Signature)

**Bài toán:** A muốn gửi một tài liệu quan trọng cho B. Làm sao B chắc chắn tài liệu đúng là của A và không bị sửa trên đường đi?

1. A băm tài liệu rồi dùng private key của mình để ký, tạo ra chữ ký.
2. A gửi tài liệu kèm chữ ký cho B.
3. B dùng public key của A để kiểm tra chữ ký với tài liệu nhận được.
4. Khớp thì tài liệu đúng là từ A và chưa bị thay đổi.

- Thuật toán dùng trong blockchain là ECDSA: chứng minh được quyền sở hữu mà không bao giờ phải gửi private key lên mạng.
- Hai lợi ích: xác thực (đúng người gửi) và toàn vẹn (dữ liệu không bị sửa khi truyền).
- Trên mạng blockchain, giao dịch được các node kiểm tra chữ ký bằng public key rồi mới được chấp nhận.

### 5. Từ private key đến địa chỉ ví (Address)

```
Private Key (256-bit)  --secp256k1-->  Public Key  --Hashing-->  Hash rút gọn  -->  Address
```

- Toàn bộ chuỗi biến đổi là một chiều, nên chia sẻ address là an toàn, còn private key thì tuyệt đối không.

### 6. Wallet (ví)

- Ví không hề chứa coin/token. Tài sản luôn nằm trên blockchain; ví chỉ quản lý cặp khóa và dùng private key để ký giao dịch.

| | Hot wallet | Cold wallet |
|---|---|---|
| Kết nối | Có internet | Khóa giữ ngoại tuyến |
| Ưu điểm | Tiện, giao dịch nhanh | An toàn hơn nếu dùng đúng, hợp lưu trữ dài hạn |
| Nhược điểm | Rủi ro bị tấn công cao hơn | Bất tiện hơn khi giao dịch |

**Seed phrase (cụm từ khôi phục)**

- Chuẩn BIP-39: 12 hoặc 24 từ tiếng Anh, từ đó sinh ra toàn bộ khóa của ví HD (BIP-32/44).
- Ai có seed phrase là kiểm soát được ví; mất seed phrase mà hỏng thiết bị thì mất ví.
- Chỉ ghi ra giấy, cất offline. Không chụp ảnh, không lưu ghi chú điện thoại hay chat, không gửi cho ai.

**Custodial vs Non-custodial**

| | Custodial | Non-custodial |
|---|---|---|
| Ai giữ private key | Bên thứ ba (sàn, dịch vụ) | Chính mình |
| Ưu điểm | Dễ dùng, quên mật khẩu vẫn khôi phục được | Toàn quyền kiểm soát tài sản |
| Nhược điểm | Phụ thuộc nền tảng và chính sách, rủi ro sàn bị hack hoặc đóng băng | Tự chịu trách nhiệm, mất seed phrase là mất hết |

### 7. Checklist bảo vệ ví cơ bản

- Không chia sẻ private key và seed phrase với bất kỳ ai.
- Cảnh giác link, trang web giả mạo và tin nhắn lừa đảo (phishing).
- Kiểm tra kỹ địa chỉ trước khi gửi vì giao dịch blockchain không hoàn lại được.
- Chỉ cài ví từ nguồn chính thức; số tiền lớn nên cân nhắc hardware wallet.
- Sao lưu seed phrase offline, tốt nhất ở nhiều nơi an toàn.

## 3. Work completed



## 4. Evidence

https://canva.link/slybut5ov0usqix

## 5. Blockers



## 6. Takeaway

