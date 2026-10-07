# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Đoàn Quang Thanh
- MSSV / mã học viên: 2A202602841
- Lớp: Track 1
- Ngành đã chọn: Mobility / autonomous driving

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | Người đi bộ, người đi xe đạp, hành khách và người tham gia giao thông khác có thể bị va chạm, chấn thương hoặc tử vong nếu hệ thống nhận diện hay dự đoán sai tình huống, hoặc xe không dừng/chuyển sang hỗ trợ an toàn khi gặp tình huống ngoài dự kiến. Người giám sát cũng có thể mất khả năng can thiệp nếu quá tin vào tự động hóa. |
| Mức độ high-stakes | Cao. Hệ thống điều khiển chuyển động của xe trên đường công cộng; một lỗi ở khâu nhận diện, dự đoán đường đi hoặc xử lý khẩn cấp có thể trực tiếp gây chấn thương nặng hoặc tử vong, như vụ Uber ATG được NTSB điều tra. Đây là đánh giá rủi ro của bài, không phải phân loại pháp lý. |
| Dữ liệu nhạy cảm có thể được sử dụng | Hình ảnh/video từ camera trong và ngoài xe, vị trí và lộ trình, dữ liệu cảm biến và telemetry, cùng dữ liệu về hành vi người lái hoặc người đi đường. Những dữ liệu này có thể nhận diện cá nhân hoặc tiết lộ vị trí và thói quen di chuyển. |
| Nhu cầu human review | Cao. Người giám sát an toàn cần theo dõi xe thử nghiệm và sẵn sàng tiếp quản; đội vận hành từ xa cần xử lý khi xe dừng hoặc tình huống không rõ; chuyên gia an toàn cần rà soát sự cố và dữ liệu trước khi cho phép tiếp tục thử nghiệm. Các bước này cần thiết vì cả nhận diện của ADS lẫn khả năng ứng phó của xe đều có giới hạn. |

### 2. Case study 1 — Uber ATG: xe thử nghiệm ADS gây tử vong cho người đi bộ ở Tempe

#### Brief Case

- Tổ chức / sản phẩm AI: Uber Advanced Technologies Group (Uber ATG), hệ thống lái tự động đang phát triển (developmental automated driving system, ADS) lắp trên xe thử nghiệm Volvo XC90.
- Thời gian, địa điểm / bối cảnh: Tối 18/03/2018, trên N. Mill Avenue ở Tempe, Arizona, Hoa Kỳ. Xe đang chạy ở chế độ tự động trong một chuyến thử nghiệm đường công cộng; một nhân viên an toàn ngồi ghế lái.
- AI được dùng để làm gì: ADS điều khiển xe và phát hiện, phân loại, dự đoán đường đi của các đối tượng trên đường trong quá trình thử nghiệm.
- Vấn đề hoặc sự kiện đáng chú ý: ADS phát hiện người đi bộ 5,6 giây trước va chạm nhưng không phân loại chính xác người này và không dự đoán được đường đi. Thiết kế hệ thống không kích hoạt phanh khẩn cấp chỉ để giảm nhẹ va chạm, mà dựa vào người giám sát can thiệp. NTSB xác định probable cause của vụ va chạm là việc người vận hành không giám sát môi trường lái và hoạt động của ADS do bị phân tâm thị giác bởi điện thoại cá nhân. Các yếu tố góp phần gồm quy trình đánh giá rủi ro an toàn chưa đầy đủ, giám sát người vận hành kém hiệu quả và thiếu biện pháp xử lý automation complacency của Uber ATG. Người đi bộ tử vong.
- Số liệu có nguồn: ADS phát hiện người đi bộ 5,6 giây trước va chạm nhưng không phân loại đúng; xe đang chạy khoảng 45 mph khi tiếp cận khu vực tai nạn và người đi bộ tử vong trong vụ va chạm. Đây là các dữ kiện của một vụ tai nạn cụ thể, không phải tỷ lệ lỗi của toàn đội xe.
- Nguồn: *Collision Between Vehicle Controlled by Developmental Automated Driving System and Pedestrian, Tempe, Arizona, March 18, 2018*, National Transportation Safety Board (NTSB), báo cáo HAR-19-03, thông qua ngày 19/11/2019, Executive Summary tr. v–vi và phần 2.2.1 “Uber ATG Safety Risk Management” tr. 39: [báo cáo điều tra NTSB (PDF)](https://www.ntsb.gov/investigations/AccidentReports/Reports/HAR1903.pdf); [trang hồ sơ điều tra NTSB](https://www.ntsb.gov/investigations/Pages/HWY18MH010.aspx).
- Phân biệt bằng chứng và nhận định: NTSB xác nhận người đi bộ tử vong, ADS không phân loại đúng và không dự đoán được đường đi, hệ thống không tự phanh để giảm nhẹ va chạm, và người vận hành bị phân tâm bởi điện thoại cá nhân. NTSB xác định probable cause là người vận hành không giám sát môi trường lái và hoạt động của ADS do bị phân tâm thị giác; cơ quan này cũng nêu các yếu tố góp phần từ đánh giá rủi ro, giám sát người vận hành và biện pháp xử lý automation complacency của Uber ATG. Nhận định về over-reliance là cách áp taxonomy GUIDE vào việc giám sát thất bại và thiếu biện pháp chống chủ quan do tự động hóa; báo cáo không kết luận người lái chủ ý giao toàn bộ trách nhiệm cho AI. Một vụ việc không cho biết tỷ lệ lỗi hay tần suất lỗi của toàn hệ thống.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi ADS đang điều khiển xe thử nghiệm trên đường đô thị và phát hiện một người đi bộ băng qua giữa đoạn đường: ADS phải phân loại và dự đoán chuyển động để quyết định phanh/đánh lái, trong khi nhân viên an toàn phải giám sát và có thể tiếp quản. Sau đó xe tiếp tục chạy tới người đi bộ. |
| Stakeholder bị ảnh hưởng | Người đi bộ bị xe tông; nhân viên an toàn trên xe; Uber ATG và cơ quan quản lý chịu trách nhiệm về thử nghiệm an toàn; những người tham gia giao thông có thể gặp rủi ro tương tự. |
| Failure mode | Over-reliance ở khâu giám sát: người lái không theo dõi đường trong lúc ADS điều khiển, và NTSB nêu thiếu cơ chế đối phó với automation complacency. Đồng thời, lỗi phân loại và dự đoán đường đi của ADS là hành vi hệ thống được báo cáo, không phải một nhãn riêng trong taxonomy GUIDE. |
| Layer bắt đầu lỗi | Model: NTSB ghi nhận ADS không phân loại đúng người đi bộ và không dự đoán đúng đường đi. Safety: thiết kế không phanh khẩn cấp để giảm nhẹ va chạm và thiếu biện pháp đủ hiệu quả để giám sát mức tập trung của người lái. NTSB cũng xác định nguyên nhân từ phía người giám sát và thiếu sót trong quản lý an toàn; không quy toàn bộ nguyên nhân cho riêng mô hình. |
| Harm xảy ra là gì? | Harm observed: người đi bộ bị xe thử nghiệm tông và tử vong. Người lái không bị thương. Đây là hậu quả được NTSB xác nhận; bài không suy ra thêm thiệt hại sức khỏe hay số người bị ảnh hưởng ngoài hồ sơ. |
| Harm lens | Injury. |
| Severity | Critical. Một người đi bộ tử vong; hậu quả thực tế là mất mạng, phù hợp mức hậu quả đặc biệt nghiêm trọng. |
| Scale | Low theo quy mô sự cố được ghi nhận: một người đi bộ tử vong trong vụ này. Không dùng số xe chạy thử hoặc số lần đi qua tuyến đường làm số người đã bị hại. |
| Probability | Chưa đủ dữ liệu để đánh giá. NTSB xác nhận kịch bản đã xảy ra trong vụ tai nạn này, nhưng báo cáo không cung cấp số tình huống tương tự hoặc mẫu số cần thiết để ước lượng xác suất. |
| Frequency | Chưa đủ dữ liệu để đánh giá. NTSB mô tả vụ tai nạn này và cho biết tuyến thử nghiệm đã được đi khoảng 50.000 lần, nhưng không cho biết lỗi phân loại/dự đoán tương tự xảy ra bao nhiêu lần. |
| Vì sao? | Severity Critical dựa trên một trường hợp tử vong được NTSB xác nhận. Scale Low chỉ mô tả số người bị hại trong sự cố cụ thể, không đại diện phạm vi rủi ro của công nghệ. Chưa đủ dữ liệu để đánh giá Probability vì NTSB không cung cấp số tình huống tương tự hoặc mẫu số; việc một kịch bản đã xảy ra không cho biết xác suất của nó. Chưa đủ dữ liệu để đánh giá Frequency: khoảng 50.000 lượt đi trên tuyến thử nghiệm không phải số lần lỗi phân loại/dự đoán xảy ra. NTSB xác định probable cause liên quan đến việc người vận hành không giám sát môi trường lái và hoạt động của ADS do bị phân tâm thị giác, đồng thời nêu các yếu tố góp phần từ đánh giá rủi ro, giám sát người vận hành và biện pháp xử lý automation complacency của ATG. |

### 3. Case study 2 — Cruise: xe tự hành kéo người đi bộ khoảng 20 feet ở San Francisco

#### Brief Case

- Tổ chức / sản phẩm AI: Cruise LLC, xe tự hành không người lái (autonomous vehicle, AV) hoạt động trong chế độ driverless ở San Francisco, California.
- Thời gian, địa điểm / bối cảnh: Khoảng 21:30 ngày 02/10/2023, tại khu vực đường 5th và Market Streets, San Francisco. Một xe do người lái điều khiển va chạm với người đi bộ trước; người này ngã vào đường đi của xe Cruise không người lái.
- AI được dùng để làm gì: Hệ thống lái tự động điều khiển xe Cruise trên đường công cộng, bao gồm phanh sau va chạm và thực hiện thao tác pullover để dừng xe.
- Vấn đề hoặc sự kiện đáng chú ý: Xe Cruise phanh và dừng sau khi va chạm với người đi bộ, sau đó thực hiện thao tác pullover khi người này vẫn mắc dưới gầm xe. Xe kéo người đi bộ thêm khoảng 20 feet với tốc độ 7 mph. CPUC cũng ghi nhận Cruise không báo đầy đủ chi tiết thao tác kéo người này trong cuộc gọi ngày 03/10 và cung cấp video đầy đủ sau yêu cầu của cơ quan quản lý.
- Số liệu có nguồn: Quyết định CPUC xác định xe Cruise kéo người đi bộ khoảng 20 feet (khoảng 6,1 m) với tốc độ 7 mph (khoảng 11,3 km/h); sự việc kéo dài 15 ngày trước khi Cruise cung cấp cho CPUC tường thuật đầy đủ. Con số 15 ngày nói về việc báo cáo, không phải thời gian người đi bộ bị kéo.
- Nguồn: *Presiding Officer’s Decision Approving Offered Settlement Terms and Granting Deferral of the Order to Show Cause Proceedings*, Decision 24-07-004, California Public Utilities Commission (CPUC), 25/07/2024, mục 1.2 tr. 4–5 và Findings of Fact 1–6 tr. 20–21: [quyết định CPUC (PDF)](https://docs.cpuc.ca.gov/PublishedDocs/Published/G000/M536/K690/536690391.PDF). Việc DMV đình chỉ giấy phép triển khai và thử nghiệm không người lái của Cruise được xác nhận trong [thông cáo California DMV ngày 24/10/2023](https://qr.dmv.ca.gov/portal/news-and-media/dmv-statement-on-cruise-llc-suspension/), các đoạn 22–29.
- Phân biệt bằng chứng và nhận định: CPUC xác nhận người đi bộ ban đầu bị một xe khác tông, ngã vào đường xe Cruise; xe Cruise sau khi dừng đã kéo người này khoảng 20 feet ở tốc độ 7 mph. California DMV xác nhận đình chỉ giấy phép vì đánh giá xe không an toàn cho công chúng và nhà sản xuất trình bày sai thông tin liên quan đến an toàn. Nguồn không xác nhận hệ thống Cruise có nhận biết người đang mắc dưới xe hay không, cũng không nêu mức độ thương tích trong quyết định được trích. Vì vậy, bài xác định thao tác pullover là lỗi vận hành có thể làm tăng nguy cơ thương tích; không khẳng định hệ thống biết người đang ở dưới xe hoặc tự gây ra va chạm ban đầu.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Sau khi người đi bộ bị xe khác tông và ngã vào xe Cruise, xe Cruise đã phanh rồi dừng; rủi ro xảy ra khi AV bắt đầu thao tác pullover trong lúc người đi bộ còn mắc dưới gầm. Hành động tiếp theo của xe làm người này bị kéo thêm. |
| Stakeholder bị ảnh hưởng | Người đi bộ trực tiếp bị xe kéo; người đi đường khác có thể gặp rủi ro ở hiện trường; đội điều khiển/hỗ trợ từ xa và Cruise chịu trách nhiệm bảo đảm xe dừng an toàn và báo cáo sự cố. |
| Failure mode | Chưa đủ bằng chứng để gán chắc một mode trong taxonomy GUIDE. Hành vi không an toàn được xác nhận là xe pullover khi người đi bộ còn dưới gầm; CPUC cũng ghi nhận xe đã liên hệ remote assistance sau khi dừng, nhưng không cho biết hệ thống có nhận ra người dưới xe hay việc hỗ trợ từ xa có thể can thiệp vào thao tác pullover hay không. Vì vậy, gọi đây là escalation failure sẽ vượt quá bằng chứng hiện có. |
| Layer bắt đầu lỗi | Chưa đủ bằng chứng công khai để xác định chắc chắn. CPUC ghi lại hành vi của AV nhưng không công bố trạng thái nội bộ, tín hiệu cảm biến hay logic khiến xe khởi động pullover. Giả thuyết phân tích: Safety, nếu điều kiện sau va chạm và yêu cầu hỗ trợ không đủ để ngăn xe di chuyển; đây chỉ là giả thuyết, không phải kết luận về kiến trúc Cruise. |
| Harm xảy ra là gì? | Harm observed: người đi bộ bị xe Cruise chạy qua và kéo thêm khoảng 20 feet. Quyết định CPUC không mô tả mức độ thương tích nên không khẳng định thương tích cụ thể. Potential harm: thao tác này có thể làm chấn thương nặng hơn. |
| Harm lens | Injury. |
| Severity | Medium theo bằng chứng hiện có: người đi bộ bị xe chạy qua và kéo ở tốc độ 7 mph, nhưng nguồn được trích không xác định mức độ thương tích. Mức này phản ánh thông tin công khai trong quyết định, không khẳng định hậu quả nhẹ. |
| Scale | Low theo sự cố được quyết định ghi nhận: một người đi bộ bị xe kéo. Không suy rộng thành số người bị ảnh hưởng bởi toàn bộ đội xe Cruise. |
| Probability | Chưa đủ dữ liệu để đánh giá. Sự cố xác nhận kịch bản AV tiếp tục di chuyển sau va chạm đã xảy ra, nhưng nguồn không cung cấp mẫu số trên số chuyến đi, số va chạm hoặc số tình huống tương tự. |
| Frequency | Chưa đủ dữ liệu để đánh giá. Nguồn được trích mô tả sự cố ngày 02/10/2023 nhưng không cung cấp tần suất các tình huống pullover sau va chạm trong toàn đội xe. |
| Vì sao? | Severity Medium là đánh giá thận trọng vì CPUC xác nhận xe kéo người đi bộ dưới gầm khoảng 20 feet ở 7 mph nhưng quyết định không nêu thương tích. Scale Low chỉ tính người bị hại trong sự cố. Chưa đủ dữ liệu để đánh giá Probability vì nguồn không cung cấp mẫu số trên số chuyến đi, số va chạm hoặc số tình huống tương tự; sự cố chỉ xác nhận kịch bản đã xảy ra. Chưa đủ dữ liệu để đánh giá Frequency vì quyết định mô tả sự cố ngày 02/10/2023 nhưng không nêu tần suất pullover sau va chạm trong toàn đội xe. Việc xe Cruise không gây ra va chạm ban đầu và khả năng hệ thống có nhận biết người mắc dưới gầm đều là giới hạn quan trọng khi quy nguyên nhân. |
