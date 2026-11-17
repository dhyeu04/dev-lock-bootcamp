
# SESSION 05 - SMART CONTRACT & DIGITAL ASSETS

- **Họ và tên:** Đỗ Duy Hiếu
- **GitHub:** [Tên tài khoản GitHub]
- **Submitted:** 17/11/2026
- **Commit:** Hợp đồng thông minh và tài sản số trên Blockchain

---

## 1. Tổng quan (Summary)

Trong Session 05, em tìm hiểu về Smart Contract (Hợp đồng thông minh) và Digital Assets (Tài sản số) trong công nghệ Blockchain.

Các nội dung chính bao gồm:

- Tìm hiểu khái niệm và nguyên lý hoạt động của Smart Contract.
- Phân biệt Native Coin và Token.
- Tìm hiểu các cơ chế Mint, Transfer và Burn.
- Nghiên cứu về Stablecoin và NFT.
- Tìm hiểu Gas Fee và Transaction Fee.
- Phân biệt các môi trường thực thi EVM, SVM và WASM.
- Liên hệ kiến thức với việc phát triển các ứng dụng Blockchain thực tế.

## 2. Nội dung kiến thức (Topic Notes)

### 2.1. Smart Contract (Hợp đồng thông minh)

Smart Contract là một chương trình được triển khai trên Blockchain, có khả năng tự động thực hiện các điều kiện và lệnh đã được lập trình trước mà không cần bên trung gian can thiệp.

**Đặc điểm:**
- Tự động thực thi khi đáp ứng điều kiện.
- Có tính minh bạch và khả năng truy xuất.
- Hoạt động trên nền tảng Blockchain.
- Dữ liệu giao dịch được ghi nhận và bảo vệ.

**Ví dụ thực tế:**

Một hệ thống bán vé sự kiện sử dụng Blockchain:
1. Người dùng thực hiện mua vé.
2. Smart Contract ghi nhận giao dịch.
3. Quyền sở hữu vé được cập nhật.
4. Lịch sử giao dịch có thể được kiểm tra trên Blockchain.

**Hạn chế:**
- Không thể tự động lấy dữ liệu bên ngoài Blockchain nếu không sử dụng Oracle.
- Lỗi lập trình có thể tạo ra lỗ hổng bảo mật.
- Việc chỉnh sửa Smart Contract sau khi triển khai có thể phức tạp.

### 2.2. Phân biệt Native Coin và Token

| Tiêu chí | Native Coin | Token |
|---|---|---|
| Khái niệm | Đồng tiền gốc của Blockchain | Tài sản được tạo trên Blockchain có sẵn |
| Cách tạo | Gắn với giao thức mạng | Thường thông qua Smart Contract |
| Công dụng | Thanh toán phí và vận hành mạng | Thanh toán, quản trị, tiện ích |
| Ví dụ | ETH, SOL | USDT, USDC |

**Ví dụ:**

Trên mạng Ethereum:
- ETH là đồng tiền gốc của Ethereum.
- USDT và USDC có thể tồn tại dưới dạng Token trên Ethereum.

### 2.3. Vòng đời của Token

Có ba thao tác quan trọng trong quá trình quản lý Token:

**1. Mint (Tạo Token)**

- Tạo ra Token mới.
- Làm tăng tổng nguồn cung.
- Cần có quyền phù hợp theo thiết kế Smart Contract.

**2. Transfer (Chuyển Token)**

- Chuyển Token từ ví này sang ví khác.
- Số dư người gửi giảm.
- Số dư người nhận tăng.
- Không làm thay đổi tổng nguồn cung.

**3. Burn (Đốt Token)**

- Loại bỏ Token khỏi nguồn cung.
- Làm giảm tổng số Token.
- Có thể được sử dụng để quản lý nguồn cung.

**Ví dụ minh họa:**

| Thao tác | Tổng nguồn cung |
|---|---:|
| Ban đầu | 100 Token |
| Mint thêm 20 Token | 120 Token |
| Transfer 10 Token | 120 Token |
| Burn 5 Token | 115 Token |

### 2.4. Stablecoin

Stablecoin là một loại tiền mã hóa được thiết kế nhằm duy trì giá trị tương đối ổn định so với một tài sản tham chiếu, phổ biến nhất là đồng USD.

**Một số Stablecoin phổ biến:**
- USDT.
- USDC.
- DAI.

**Các loại Stablecoin:**

1. Fiat-backed: Được bảo chứng bằng tiền pháp định hoặc tài sản dự trữ.
2. Crypto-collateralized: Được bảo đảm bằng các tài sản mã hóa khác.
3. Algorithmic: Sử dụng thuật toán để điều chỉnh cung và cầu.

**Depeg là gì?**

Depeg là hiện tượng Stablecoin bị mất hoặc lệch khỏi mức giá trị tham chiếu.

Ví dụ: Một Stablecoin được thiết kế để duy trì giá trị 1 USD nhưng giá thị trường giảm xuống 0,97 USD.

### 2.5. NFT (Non-Fungible Token)

NFT là một loại Token không thể thay thế, mỗi NFT có mã định danh riêng biệt để phân biệt với những NFT khác.

**Đặc điểm:**
- Mỗi NFT có định danh riêng.
- Có thể đại diện cho tài sản kỹ thuật số.
- Có thể chuyển nhượng giữa các ví.
- Lịch sử giao dịch được ghi nhận trên Blockchain.

**Ứng dụng thực tế:**
- Tranh ảnh kỹ thuật số.
- Vật phẩm trong trò chơi.
- Vé tham gia sự kiện.
- Tài sản sưu tầm.
- Chứng nhận kỹ thuật số.

Lưu ý: Việc sở hữu NFT không đồng nghĩa với việc tự động sở hữu bản quyền của tác phẩm được NFT đại diện.

### 2.6. Gas Fee và Transaction Fee

Gas là đơn vị đo lượng tài nguyên tính toán cần thiết để thực hiện một giao dịch trên Blockchain.

**Công thức tính phí cơ bản:**

`Transaction Fee = Gas Used × Gas Price`

Trong đó:

- Gas Used: Lượng Gas thực tế được sử dụng.
- Gas Price: Đơn giá Gas.
- Transaction Fee: Tổng phí giao dịch.

**Ví dụ:**

- Gas Used = 21.000.
- Gas Price = 20 Gwei.
- 1 Gwei = 0,000000001 ETH.

Phí giao dịch:

`21.000 × 20 × 0,000000001 = 0,00042 ETH`

**Một số lưu ý:**
- Giao dịch phức tạp thường tiêu tốn nhiều Gas hơn.
- Khi mạng lưới đông, phí giao dịch có thể tăng.
- Giao dịch bị Revert vẫn có thể mất phí Gas.

### 2.7. Các môi trường thực thi Blockchain

| Môi trường | Tên đầy đủ | Đặc điểm |
|---|---|---|
| EVM | Ethereum Virtual Machine | Môi trường thực thi Smart Contract của Ethereum và các mạng tương thích |
| SVM | Solana Virtual Machine | Môi trường thực thi chương trình trong hệ sinh thái Solana |
| WASM | WebAssembly | Công nghệ thực thi mã đa nền tảng được một số Blockchain sử dụng |

**EVM:**
- Phổ biến trong hệ sinh thái Ethereum.
- Hỗ trợ Smart Contract viết bằng Solidity.
- Có thể sử dụng Remix IDE để phát triển và triển khai.

**SVM:**
- Được sử dụng trong hệ sinh thái Solana.
- Hỗ trợ thực thi các chương trình trên Solana.

**WASM:**
- Hỗ trợ nhiều ngôn ngữ lập trình.
- Có khả năng thực thi trên nhiều nền tảng.
- Được sử dụng trong một số hệ sinh thái Blockchain.

## 3. Ứng dụng thực tế (Practical Application)

### 3.1. Liên hệ với dự án PortablePass

Trong quá trình tìm hiểu và phát triển dự án PortablePass, em nhận thấy Smart Contract có thể đóng vai trò quan trọng trong việc quản lý tài liệu và xác minh quyền sở hữu.

Một số ứng dụng có thể triển khai:

- Lưu trữ thông tin định danh tài liệu trên Blockchain.
- Quản lý quyền truy cập tài liệu thông qua địa chỉ ví.
- Ghi nhận lịch sử thay đổi và chuyển giao quyền sở hữu.
- Kiểm tra tính hợp lệ của các thao tác thông qua Smart Contract.

### 3.2. Quy trình làm việc với Smart Contract

Quy trình triển khai cơ bản:

1. Viết mã nguồn Smart Contract bằng Solidity.
2. Sử dụng Remix IDE để biên dịch mã nguồn.
3. Lựa chọn môi trường triển khai phù hợp.
4. Kết nối ví MetaMask.
5. Triển khai Smart Contract.
6. Kiểm tra địa chỉ Contract sau khi triển khai.
7. Thử nghiệm các hàm và kiểm tra kết quả giao dịch.

Thông qua quy trình này, em hiểu rõ hơn mối liên hệ giữa Smart Contract, ví Blockchain và giao diện ứng dụng.

## 4. Work Completed

- Tìm hiểu kiến thức cơ bản về Smart Contract.
- Phân biệt Native Coin và Token.
- Nắm được cơ chế Mint, Transfer và Burn.
- Tìm hiểu về Stablecoin và NFT.
- Nghiên cứu công thức tính Gas Fee.
- Phân biệt các môi trường EVM, SVM và WASM.
- Liên hệ kiến thức với dự án PortablePass.
- Tổng hợp kiến thức thành tài liệu Session 05.

## 5. Evidence

Các minh chứng có thể bổ sung:

- Ảnh chụp ghi chú và tài liệu học tập.
- Ảnh giao diện Remix IDE.
- Ảnh quá trình biên dịch Smart Contract.
- Ảnh kết nối ví MetaMask.
- Ảnh kết quả triển khai hoặc tương tác với Contract.

## 6. Blockers


## 7. Takeaways


