## README - Dữ liệu Hành chính Việt Nam (Sau Sáp nhập 2025) - Phiên bản Tiếng Việt

### Giới thiệu

Đây là bộ dữ liệu chính về các đơn vị hành chính cấp tỉnh và cấp xã (phường/thị trấn/xã) của Việt Nam, được chuẩn hóa và cập nhật sau quá trình sáp nhập, tổ chức lại các đơn vị hành chính theo Nghị quyết của Chính phủ, dự kiến chính thức đi vào hoạt động trong tháng 7 năm 2025.

Bộ dữ liệu này cung cấp thông tin chi tiết cho **34 tỉnh/thành phố** đã được sáp nhập và tổ chức lại.

Chúng tôi cung cấp bộ dữ liệu này dưới hai định dạng chính để phục vụ các nhu cầu sử dụng khác nhau:

1.  **Dữ liệu Nested (Lồng ghép):** Định dạng gốc, phản ánh cấu trúc phân cấp hành chính tự nhiên (tỉnh/thành phố chứa các quận/huyện, và quận/huyện chứa các xã/phường/thị trấn). (Ví dụ: `nested-province-2025.json`)
2.  **Dữ liệu Flattened (Làm phẳng):** Định dạng đã được xử lý để làm phẳng cấu trúc, trong đó mỗi bản ghi cấp xã sẽ mang theo đầy đủ thông tin của tỉnh/thành phố mà nó thuộc về, giúp dễ dàng truy vấn và tích hợp. (Ví dụ: `flattened_provinces.json`)

### Cấu trúc Dữ liệu

#### 1\. Dữ liệu Nested (`nested-province-2025.json`)

File này chứa cấu trúc lồng ghép, mỗi đối tượng cấp tỉnh/thành phố sẽ có một mảng `wards` (xã/phường/thị trấn) bên trong.

**Ví dụ:**

```json
[
    {
        "code": "01",
        "name": "Thành phố Hà Nội",
        "division_type": "city",
        "merged_from": [],
        "wards": [
            {
                "code": "00070",
                "name": "Phường Hoàn Kiếm",
                "division_type": "Phường"
            },
            // ... các phường/xã khác của Hà Nội
        ]
    },
    // ... các tỉnh/thành phố khác
]
```

#### 2\. Dữ liệu Flattened (`flattened_provinces.json`)

Dữ liệu này được tổ chức dưới dạng danh sách các đối tượng JSON, mỗi đối tượng đại diện cho một đơn vị hành chính cấp xã cùng với thông tin tỉnh/thành phố mà nó thuộc về.

Mỗi đối tượng có các trường sau:

  * `city_code`: Mã đơn vị hành chính cấp tỉnh/thành phố.
  * `city_name`: Tên đơn vị hành chính cấp tỉnh/thành phố.
  * `city_division_type`: Loại hình đơn vị hành chính cấp tỉnh/thành phố (ví dụ: "city", "province").
  * `merged_from`: Danh sách các đơn vị hành chính đã được sáp nhập để hình thành đơn vị hành chính hiện tại (nếu có).
  * `ward_code`: Mã đơn vị hành chính cấp xã (phường/thị trấn/xã).
  * `ward_name`: Tên đơn vị hành chính cấp xã.
  * `ward_division_type`: Loại hình đơn vị hành chính cấp xã (ví dụ: "Phường", "Xã", "Thị trấn").

**Ví dụ một bản ghi:**

```json
{
    "city_code": "01",
    "city_name": "Thành phố Hà Nội",
    "city_division_type": "city",
    "merged_from": [],
    "ward_code": "00070",
    "ward_name": "Phường Hoàn Kiếm",
    "ward_division_type": "Phường"
}
```

### Cách sử dụng

Dữ liệu có thể được sử dụng cho nhiều mục đích khác nhau như:

  * Phát triển các ứng dụng có tính năng chọn địa điểm theo phân cấp hành chính.
  * Phân tích dữ liệu dân cư, kinh tế theo từng khu vực.
  * Cập nhật hệ thống master data hành chính cho các doanh nghiệp, tổ chức.
  * Nghiên cứu về cơ cấu và sự thay đổi của các đơn vị hành chính tại Việt Nam.

### Đóng góp và Phản hồi

Chúng tôi hoan nghênh mọi ý kiến đóng góp, phản hồi hoặc đề xuất cải thiện về bộ dữ liệu này. Nếu bạn phát hiện bất kỳ thông tin nào chưa chính xác hoặc có gợi ý để làm cho bộ dữ liệu hữu ích hơn, xin vui lòng liên hệ hoặc tạo một [issue/pull request trên GitHub](LIÊN KẾT GITHUB CỦA BẠN NẾU CÓ).

### Lưu ý Quan trọng (Disclaimer)

**Người tạo và phát hành bộ dữ liệu này không chịu trách nhiệm về bất kỳ rủi ro, thiệt hại hoặc mất mát nào phát sinh từ việc sử dụng dữ liệu này.**

Mặc dù chúng tôi đã nỗ lực hết sức để đảm bảo tính chính xác và cập nhật của dữ liệu dựa trên các thông tin công khai tại thời điểm xây dựng, nhưng do tính chất thay đổi liên tục của các quy định hành chính và quá trình triển khai sáp nhập, **khả năng có sai sót là không thể tránh khỏi.**

**Người sử dụng hoàn toàn chịu trách nhiệm về việc kiểm tra, xác minh tính chính xác của dữ liệu trước khi sử dụng cho bất kỳ mục đích nào, đặc biệt là các mục đích quan trọng hoặc yêu cầu độ chính xác cao.** Chúng tôi khuyến khích người dùng tham khảo các nguồn thông tin chính thức của cơ quan nhà nước khi có nhu cầu.

-----

## README - Vietnam Administrative Data (Post-Merger 2025) - English Version

### Introduction

This is the official dataset of administrative units at the provincial and commune (ward/township/commune) levels in Vietnam, standardized and updated following the restructuring and merger of administrative units according to government resolutions, expected to officially come into operation on July 1, 2025.

This dataset provides detailed information for **34 provinces/cities** that have undergone mergers and restructuring.

We provide this dataset in two main formats to serve different usage needs:

1.  **Nested Data:** The original format, reflecting the natural hierarchical administrative structure (provinces/cities containing districts/rural districts, and districts/rural districts containing communes/wards/townships). (Example: `nested-province-2025.json`)
2.  **Flattened Data:** A processed format where the structure has been flattened. Each commune-level record will carry complete information about the province/city it belongs to, making it easy for querying and integration. (Example: `flattened_provinces.json`)

### Data Structure

#### 1\. Nested Data (`nested-province-2025.json`)

This file contains a nested structure, where each province/city object will have a `wards` array (communes/wards/townships) within it.

**Example:**

```json
[
    {
        "code": "01",
        "name": "Thành phố Hà Nội",
        "division_type": "city",
        "merged_from": [],
        "wards": [
            {
                "code": "00070",
                "name": "Phường Hoàn Kiếm",
                "division_type": "Phường"
            },
            // ... other wards/communes of Hanoi
        ]
    },
    // ... other provinces/cities
]
```

#### 2\. Flattened Data (`flattened_provinces.json`)

This data is organized as a list of JSON objects, with each object representing a commune-level administrative unit along with the province/city information it belongs to.

Each object includes the following fields:

  * `city_code`: Code of the provincial/city-level administrative unit.
  * `city_name`: Name of the provincial/city-level administrative unit.
  * `city_division_type`: Type of the provincial/city-level administrative unit (e.g., "city", "province").
  * `merged_from`: A list of administrative units that were merged to form the current administrative unit (if applicable).
  * `ward_code`: Code of the commune-level administrative unit (ward/township/commune).
  * `ward_name`: Name of the commune-level administrative unit.
  * `ward_division_type`: Type of the commune-level administrative unit (e.g., "Phường" (Ward), "Xã" (Commune), "Thị trấn" (Township)).

**Example record:**

```json
{
    "city_code": "01",
    "city_name": "Thành phố Hà Nội",
    "city_division_type": "city",
    "merged_from": [],
    "ward_code": "00070",
    "ward_name": "Phường Hoàn Kiếm",
    "ward_division_type": "Phường"
}
```

### Usage

This data can be used for various purposes such as:

  * Developing applications with administrative location selection features.
  * Analyzing demographic and economic data by region.
  * Updating administrative master data systems for businesses and organizations.
  * Researching the structure and changes of administrative units in Vietnam.

### Contributions and Feedback

We welcome all contributions, feedback, or suggestions for improving this dataset. If you find any inaccurate information or have suggestions to make the dataset more useful, please feel free to contact us or create an [issue/pull request on GitHub](https://www.google.com/search?q=YOUR_GITHUB_LINK_IF_ANY).

### Important Note (Disclaimer)

**The creator and publisher of this dataset are not responsible for any risks, damages, or losses arising from the use of this data.**

While every effort has been made to ensure the accuracy and timeliness of the data based on publicly available information at the time of its creation, due to the constantly evolving nature of administrative regulations and the ongoing merger implementation process, **errors are unavoidable.**

**Users are solely responsible for verifying the accuracy of the data before using it for any purpose, especially for critical purposes or those requiring high precision.** We encourage users to refer to official government sources when necessary.

-----
