# Session 04 - Cơ chế đồng thuận & Kiến trúc Blockchain

- **Student:** Đỗ Duy Hiếu
- **GitHub:** <điền link GitHub của bạn>
- **Submitted:** 10/11/2026
- **Commit:** <điền link commit/repo của bạn>

---

## 1. Summary

Bài học xoay quanh một câu hỏi: **một mạng không có máy chủ trung tâm, các node không tin nhau, thì làm sao thống nhất được một sổ cái duy nhất?** Câu trả lời gồm 6 phần:

1. Cơ chế đồng thuận & bài toán Byzantine
2. PoW vs PoS & tính chung cuộc (finality)
3. Bộ ba bất khả thi & Layer 1 / Layer 2
4. Account-based vs UTXO
5. Ba mô hình triển khai: Public / Private / Permissioned
6. Ca ứng dụng: cấp bằng đại học trên blockchain

---

## 2. Topic notes

### 2.1. Đồng thuận & bài toán Byzantine

- **Đồng thuận (consensus)** là cách các node phân tán cùng đi đến một trạng thái sổ cái chung, dù có node bị lỗi hoặc cố tình gian lận.
- Gốc của vấn đề là **bài toán các vị tướng Byzantine**: nhiều vị tướng phải cùng quyết định tấn công hay rút lui, nhưng trong số họ có kẻ phản bội gửi tin sai.
- Mạng chịu lỗi Byzantine chỉ an toàn khi số node xấu **chưa tới 1/3** tổng số node. Công thức hay gặp: cần ít nhất **n ≥ 3f + 1** node để chịu được **f** node xấu (ví dụ chịu 1 node xấu thì cần tối thiểu 4 node).
- Mỗi cơ chế đồng thuận đều phải trả lời 2 câu hỏi:
  - **Ai** được đề xuất block tiếp theo?
  - **Làm sao** mạng chấp nhận block đó?

```
[Node 1]  \
[Node 2]  ---> (Đồng thuận) ---> [ SỔ CÁI CHUNG DUY NHẤT ]
[Node 3]  /
[Node xấu] ... bị loại, không ảnh hưởng kết quả
```

### 2.2. Proof of Work (PoW) vs Proof of Stake (PoS)

**PoW - cạnh tranh bằng sức tính toán**
- Thợ đào (miner) lặp lại: thử một *nonce* → băm block → so với *target*. Hash nhỏ hơn target là thành công.
- Ai tìm ra trước thì được thêm block và nhận thưởng.

```
[Thử nonce] -> [Băm block] -> [So với target]
     ^                              |
     |------ hash >= target --------|   (hash < target: thành công)
```

**PoS - bảo đảm bằng tài sản ký quỹ**
- Validator khóa (stake) coin làm tài sản đảm bảo.
- Một validator được chọn đề xuất block, các validator khác kiểm tra.
- Gian lận thì bị **slashing** (bị cắt coin đã ký quỹ).

| Tiêu chí | PoW | PoS |
|---|---|---|
| Tài nguyên | Điện năng + máy đào | Coin ký quỹ |
| Người tạo block | Miner | Validator |
| An ninh dựa vào | Chi phí tính toán | Nguy cơ bị slashing |
| Năng lượng | Cao | Thấp hơn nhiều |
| Finality | Theo xác suất | Thường nhanh và xác định hơn |
| Ví dụ | Bitcoin | Ethereum, Cardano |

### 2.3. Tính chung cuộc (Finality)

- **Finality** là thời điểm giao dịch chắc chắn và không thể bị đảo ngược.
- Giao dịch vừa nằm trong block thì chưa chắc chắn tuyệt đối.
- **Theo xác suất (Bitcoin):** càng nhiều block xếp lên sau, khả năng bị đảo ngược càng thấp. Thường chờ khoảng 6 xác nhận.
- **Xác định (Ethereum):** khi đủ đa số validator xác nhận và block được finalize thì giao dịch được chốt.

```
[TX] -> [+1] -> [+2] -> [+3] -> ... -> [+6]
 xác suất bị đảo ngược giảm dần  ------>  coi như chung cuộc
```

### 2.4. Bộ ba bất khả thi & Layer 1 / Layer 2

- **Blockchain Trilemma:** rất khó đạt cùng lúc 3 thứ: **Phi tập trung**, **Bảo mật**, **Khả năng mở rộng**. Tăng thứ này thường phải hy sinh thứ kia.
- **Layer 1:** tầng gốc lo đồng thuận, dữ liệu, bảo mật (Bitcoin, Ethereum).
- **Layer 2:** tầng mở rộng, xử lý nhanh bằng cách gom nhiều giao dịch off-chain rồi gửi kết quả đã nén về Layer 1 (Lightning Network, Arbitrum, Optimism).
- **Ví dụ dễ nhớ:** Layer 1 là đường cao tốc chính, Layer 2 là các đường gom xử lý bớt xe rồi mới nhập về cao tốc.

### 2.5. Account-based vs UTXO

| | Account-based (Ethereum) | UTXO (Bitcoin) |
|---|---|---|
| Ví dụ đời thường | Số dư tài khoản ngân hàng | Những tờ tiền chưa tiêu |
| Cách hoạt động | Trừ/cộng trực tiếp vào số dư | Dùng input cũ, tạo output mới |

- **Account-based:** An có 100, Bình có 20. An gửi Bình 30 → An còn 70, Bình thành 50.
- **UTXO:** An dùng 2 tờ 50 (tổng 100) để gửi Bình 70 → tạo 2 output: 70 cho Bình và **30 tiền thối** trả lại cho An. Hai tờ 50 cũ coi như đã tiêu.

### 2.6. Ba mô hình triển khai

| Tiêu chí | Public | Private | Permissioned |
|---|---|---|---|
| Ai kiểm soát | Không ai riêng lẻ, mở cho mọi người | Một tổ chức | Liên minh nhiều tổ chức |
| Quyền đọc | Công khai | Giới hạn | Tùy chính sách |
| Quyền ghi | Không cần cấp phép | Nội bộ | Chỉ thành viên được cấp quyền |
| Tin cậy dựa vào | Kinh tế của mạng | Tổ chức đó | Nhiều bên cùng giám sát |
| Ví dụ | Bitcoin, Ethereum | Mạng nội bộ doanh nghiệp | Hyperledger Fabric |

### 2.7. Ca ứng dụng: cấp bằng đại học

- Các trường lập **liên minh** và vận hành một **Permissioned chain** để cấp, quản lý, thu hồi bằng.
- Định kỳ lấy **Merkle Root** của cả lô bằng rồi **neo (anchor)** lên một **Public chain**.
- **Không đưa dữ liệu cá nhân lên chain.** Dữ liệu trên chain công khai gần như không xóa được, nên chỉ lưu bằng chứng mã hóa (Merkle Root). Nhà tuyển dụng vẫn kiểm chứng được văn bằng có thật và chưa bị sửa.

```
[Trường A] \
[Trường B] --- Quản trị chung ---> [ CHUỖI LIÊN MINH (Permissioned) ]
[Trường C] /                                   |
                                    neo Merkle Root định kỳ
                                               v
                                    [ PUBLIC CHAIN ] <- ai cũng kiểm chứng được
```

### 2.8. Trả lời câu hỏi ôn tập

1. **Vì sao blockchain cần cơ chế đồng thuận?**
   Vì không có máy chủ trung tâm và các node không tin nhau. Đồng thuận giúp cả mạng thống nhất một sổ cái duy nhất và chặn gian lận chi tiêu kép (double-spending), kể cả khi có node lỗi hoặc nói dối.
2. **Miner (PoW) và validator (PoS) khác nhau thế nào?**
   Miner cạnh tranh bằng phần cứng và điện năng để tìm nonce. Validator khóa coin làm tài sản đảm bảo, làm sai thì bị slashing.
3. **Finality theo xác suất khác finality xác định ra sao?**
   Theo xác suất: chờ càng nhiều block thì càng yên tâm, nhưng không bao giờ tuyệt đối. Xác định: khi đủ đa số validator xác nhận thì giao dịch được chốt hẳn.
4. **Trilemma là gì, Layer 2 giải quyết thế nào?**
   Một chuỗi khó có đủ phi tập trung, bảo mật và mở rộng cùng lúc. Layer 2 xử lý giao dịch off-chain nhanh và rẻ, chỉ gửi kết quả nén về Layer 1 để thừa hưởng bảo mật của Layer 1.
5. **Vì sao không đưa thông tin cá nhân lên Public blockchain khi cấp bằng?**
   Dữ liệu trên chain công khai và gần như không xóa được, nên lộ thông tin cá nhân là vi phạm riêng tư nghiêm trọng. Chỉ lưu Merkle Root làm bằng chứng là đủ để kiểm chứng.

---

## 3. Work completed



## 4. Evidence



## 5. Blockers



## 6. Takeaway

- Đồng thuận kết hợp toán học mật mã với động lực kinh tế (thưởng và phạt) để giữ trật tự cho hệ thống không có người quản lý trung tâm.
- Chia tầng Layer 1 + Layer 2 giúp mở rộng quy mô mà không làm yếu phần bảo mật cốt lõi.
- Với dữ liệu nhạy cảm, nên để dữ liệu thật ngoài chain và chỉ neo bằng chứng (hash / Merkle Root) lên chain công khai.
