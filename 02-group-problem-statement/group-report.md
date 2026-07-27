# Group Report — Day 02

## 0. Thành viên nhóm

> Danh sách chỉ giữ họ tên, mã học viên và đầu việc cần thiết cho bài lab; không đưa số điện thoại hoặc thông tin liên hệ cá nhân vào report.

| STT | Họ và tên | Mã học viên | Vai trò và đầu việc phụ trách |
|---:|---|---|---|
| 1 | Nguyễn Thị Xuân Mai | 2A202601691 | **Thư ký nhóm:** ghi biên bản pitch/challenge, tổng hợp candidates và lưu bằng chứng thảo luận |
| 2 | Lưu Quang Nhật | 2A202601920 | **Group Convergence:** gom cluster, lập shortlist và tổng hợp scorecard Phase 3 |
| 3 | Đoàn Minh Hiếu | 2A202601733 | **Phỏng vấn người dùng:** chuẩn bị câu hỏi, thực hiện phỏng vấn và tổng hợp tín hiệu xác nhận/phản bác |
| 4 | Kim Mạnh Hưng | 2A202601679 | **Survey và baseline:** triển khai khảo sát, thu log tác vụ và tính thời gian tra cứu hiện tại |
| 5 | Trần Đoàn Hưng | 2A202601143 | **Audit dữ liệu văn bản:** kiểm tra metadata, phiên bản, hiệu lực và quan hệ sửa đổi/thay thế |
| 6 | Lê Tuấn Hiệp | 2A202601667 | **Research giải pháp:** tìm công cụ/pattern tương tự, kiểm nguồn và rút ra bài học cho nhóm |
| 7 | Ngô Khánh Trượng | 2A202601477 | **Current Workflow:** mô tả actor, input/output, handoff, thời gian và bottleneck hiện tại |
| 8 | Phùng Văn Linh | 2A202601992 | **Nhóm trưởng/Decision owner:** điều phối tiến độ, xử lý bất đồng, dẫn thảo luận và chốt quyết định nhóm |
| 9 | Cao Hữu Phúc | 2A202601283 | **Future Workflow:** thiết kế điểm can thiệp Rule/AI, human review, fallback và rollback |
| 10 | Đinh Lê Quỳnh Phương | 2A202601865 | **Problem Statement và Metrics:** hoàn thiện v0/v1, baseline, target và cách đo |
| 11 | Nguyễn Ngọc Sơn | 2A202601948 | **Risk, Boundary và QA:** kiểm tra phân quyền, citation, giới hạn AI và rà report theo rubric |

## 1. Trạng thái bằng chứng

Nhóm đã chốt candidate:

```text
Tra cứu đúng văn bản/quy chế nội bộ đang có hiệu lực — “PolicyMate AI”.
```

Tại thời điểm lập báo cáo, dữ liệu có sẵn mới xác nhận:

- danh sách và vai trò của 11 thành viên;
- log Problem Scan được chuẩn hóa thành 11 candidate problems của 11 thành viên;
- kết quả cluster, shortlist và scorecard hội tụ được tổng hợp ở Phase 3;
- candidate PolicyMate đã được nhóm chọn;
- thực trạng ban đầu: lãnh đạo, nhân viên và giảng viên mất nhiều thời gian tìm đúng văn bản/quy chế đang có hiệu lực trong kho nội bộ phân tán;
- mục tiêu định hướng: độ chính xác nội dung tối thiểu 85% và giảm ít nhất 50% thời gian tìm thông tin;
- các ràng buộc bắt buộc: grounded trên văn bản chính thức, citation rõ, phân quyền, người dùng chịu trách nhiệm quyết định cuối.

Chưa có trong repo:

- biên bản lời pitch/challenge nguyên văn của từng thành viên;
- log tra cứu, survey hoặc phỏng vấn người dùng;
- mẫu kho văn bản và baseline thời gian.

Vì vậy, Phase 3 được hoàn thiện từ log đã cung cấp và danh sách thành viên của nhóm. Các kết quả validation chưa được điền bằng dữ liệu giả; những con số chưa đo được ghi rõ là mục tiêu hoặc giả thuyết.

---

# 2. Phase 3 — Group Convergence

## 2.1. Tổng hợp candidates từ log thành viên

Nhóm chuẩn hóa nội dung pitch thành các candidate problems theo cùng cấu trúc: người gặp vấn đề, bottleneck và cảm nhận ban đầu. Các candidate gần nhau vẫn được giữ ở bước này; việc gom trùng được thực hiện ở bước cluster.

| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---:|---|---|---|---|---|
| 1 | Nguyễn Thị Xuân Mai | Search theo từ khóa trả về nhiều tài liệu nhưng không chỉ ra chính xác điều khoản liên quan | Lãnh đạo, nhân viên và giảng viên cần tra cứu quy định | Phải mở nhiều tài liệu, tự đọc và đối chiếu để tìm đúng điều/khoản | Actor và workflow rõ; đo được bằng thời gian tra cứu và tỷ lệ tìm đúng |
| 2 | Lưu Quang Nhật | Người dùng không được cảnh báo khi văn bản sắp hết hiệu lực hoặc đã có văn bản thay thế | Người tra cứu và người sử dụng kết quả nghiệp vụ | Thiếu kiểm soát phiên bản, ngày hiệu lực và quan hệ thay thế giữa văn bản | Tác động nghiệp vụ lớn; cần audit metadata và cơ chế version control |
| 3 | Đoàn Minh Hiếu | Cùng một quy định được các phòng ban hiểu và giải thích không thống nhất | Chuyên viên tư vấn, phòng ban nhận tư vấn và người ra quyết định | Thiếu một nguồn diễn giải có căn cứ; phải hỏi lại hoặc xác nhận nhiều lần | Impact rộng nhưng metric chất lượng khó hơn; cần case thực tế để kiểm chứng |
| 4 | Kim Mạnh Hưng | Khó xây dựng roadmap học tập phù hợp cho từng cá nhân | Người học có mục tiêu, năng lực và quỹ thời gian khác nhau | Phải tự nối mục tiêu, trình độ, thời gian và tài liệu thành lộ trình | AI có thể cá nhân hóa, nhưng độ phù hợp khó đánh giá khách quan |
| 5 | Trần Đoàn Hưng | Người học không biết nên bắt đầu học từ đâu | Người mới học một lĩnh vực hoặc kỹ năng | Không biết đánh giá điểm xuất phát và chọn nội dung ưu tiên | Pain gần gũi; cần xác định domain học tập cụ thể |
| 6 | Lê Tuấn Hiệp | Người học không biết mình còn thiếu kỹ năng nào | Sinh viên và người đi làm muốn phát triển năng lực | Khái niệm “kỹ năng còn thiếu” mơ hồ nếu không có chuẩn năng lực đích | Tác động rộng nhưng actor, chuẩn đánh giá và metric chưa đủ chặt |
| 7 | Ngô Khánh Trượng | Văn bản nội bộ nằm rải rác ở nhiều thư mục và định dạng nên khó xác định đâu là nguồn chính thức | Nhân viên, giảng viên và người quản trị văn bản | Phải tìm qua nhiều nguồn, tên file không thống nhất và có tài liệu trùng lặp | Pain xảy ra trước cả bước AI; cần chuẩn hóa kho và metadata |
| 8 | Phùng Văn Linh | Kết quả tra cứu không kèm số hiệu, điều/khoản và đoạn nguồn để người dùng kiểm tra | Người sử dụng câu trả lời để xử lý nghiệp vụ hoặc ra quyết định | Phải tìm lại tài liệu gốc; khó biết câu trả lời dựa trên căn cứ nào | Citation là boundary bắt buộc và có metric rõ |
| 9 | Cao Hữu Phúc | Công cụ tìm kiếm có thể trả về tài liệu mà người dùng không có thẩm quyền xem | Người dùng có các vai trò và phạm vi truy cập khác nhau | Quyền của tài liệu gốc không được giữ nguyên trong lớp tìm kiếm/trợ lý | Rủi ro cao; cần permission filter và kiểm thử truy cập vượt quyền |
| 10 | Đinh Lê Quỳnh Phương | Văn bản scan hoặc khác định dạng khiến nội dung và metadata được trích xuất không đầy đủ | Người quản trị kho và người tra cứu | OCR sai, mất số hiệu/điều khoản hoặc chia đoạn không đúng làm retrieval sai | Cần audit chất lượng dữ liệu trước khi đặt target AI |
| 11 | Nguyễn Ngọc Sơn | Không có log để truy vết người dùng đã nhận câu trả lời nào và dựa trên phiên bản văn bản nào | Quản trị hệ thống, chuyên viên nghiệp vụ và người kiểm tra | Khó điều tra khi có citation sai, văn bản đổi hiệu lực hoặc phát sinh khiếu nại | Audit log quan trọng cho vận hành nhưng cần bảo vệ dữ liệu nhạy cảm |

> Candidates #1–#6 được chuẩn hóa trực tiếp từ hai log đã cung cấp. Candidates #7–#11 là các vấn đề nhóm bổ sung khi challenge scope PolicyMate; từng thành viên cần xác nhận lại đúng nội dung mình đã đóng góp trước khi nộp.

### Tín hiệu quan trọng sau khi nghe pitch

- Các candidate về nguồn dữ liệu, search, citation, hiệu lực và cách diễn giải không phải các sản phẩm riêng biệt mà là pain liên tiếp trong cùng workflow tra cứu văn bản: **tìm đúng nguồn → tìm đúng điều khoản → xác định đúng hiệu lực → kiểm tra căn cứ → hiểu và áp dụng nhất quán**.
- Ba candidate học tập cùng nằm trong bài toán cá nhân hóa lộ trình, nhưng còn thiếu domain cụ thể, chuẩn năng lực và cách đánh giá một roadmap là phù hợp.
- Hai candidate về phân quyền và audit log là ràng buộc vận hành bắt buộc nếu PolicyMate dùng tài liệu nội bộ.
- Nhóm không chọn candidate chỉ vì “AI có thể làm”, mà ưu tiên actor rõ, workflow có thể vẽ, bottleneck cụ thể và metric có thể đo.

## 2.2. Gom nhóm / cluster

| Cluster | Candidates included | Pattern chung | Ghi chú |
|---|---|---|---|
| A — Nguồn dữ liệu và tra cứu đúng căn cứ | #1 Tìm đúng điều/khoản; #7 Nguồn phân tán; #8 Thiếu citation; #10 OCR/định dạng | Search từ khóa trả nhiều kết quả; dữ liệu phân tán hoặc trích xuất lỗi khiến người dùng vẫn phải tự đọc và xác minh | Cần process fix, metadata và data-quality gate trước khi dùng AI retrieval |
| B — Quản trị hiệu lực và diễn giải | #2 Cảnh báo văn bản hết hiệu lực/thay thế; #3 Giải thích không thống nhất | Tìm được tài liệu chưa đủ; phải biết phiên bản nào áp dụng và giải thích trên cùng căn cứ | Version control và human review quan trọng hơn việc chỉ thêm chatbot |
| C — Lộ trình học tập cá nhân | #4 Roadmap cá nhân; #5 Không biết bắt đầu; #6 Không biết thiếu kỹ năng gì | Người học thiếu một quá trình đánh giá điểm xuất phát, khoảng cách kỹ năng và bước học tiếp theo | Cần thu hẹp theo một nghề/kỹ năng và xây chuẩn đánh giá trước |
| D — Bảo mật và khả năng truy vết | #9 Truy cập vượt quyền; #11 Thiếu audit log | Trợ lý dùng tài liệu nội bộ phải giữ nguyên quyền truy cập và truy vết được nguồn/phiên bản của từng câu trả lời | Đây là boundary vận hành bắt buộc, không phải tính năng phụ |

### Kết quả gom nhóm

Nhóm hợp nhất Cluster A, B và D thành candidate:

```text
PolicyMate — hỗ trợ tra cứu đúng văn bản/quy chế đang có hiệu lực,
trích dẫn chính xác điều/khoản và cảnh báo khi nguồn có thể đã hết hiệu lực
hoặc bị thay thế.
```

Boundary ban đầu: PolicyMate hỗ trợ tra cứu và tạo bản nháp có căn cứ; không tự thay người có thẩm quyền diễn giải hoặc ra quyết định cuối.

## 2.3. Shortlist của nhóm

| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| **PolicyMate — tra cứu đúng điều khoản và phiên bản có hiệu lực** | Gộp được hai pain có quan hệ chặt: search không chỉ đúng điều khoản và thiếu cảnh báo hiệu lực. Actor/workflow rõ, tác động trực tiếp đến vận hành, có thể đo thời gian, correctness, citation và lỗi version | Chưa xác nhận baseline, quyền truy cập, chất lượng OCR/metadata và quan hệ sửa đổi/thay thế trong dữ liệu thật |
| **Hỗ trợ giải thích quy định nhất quán giữa các phòng ban** | Tác động đến cả người tư vấn và người nhận tư vấn; có thể giảm số lần hỏi lại và mâu thuẫn khi áp dụng | “Giải thích đúng” phụ thuộc thẩm quyền và bối cảnh; AI không được trở thành nguồn tư vấn cuối; chưa có case cụ thể để đo |
| **Roadmap học tập cá nhân dựa trên khoảng cách kỹ năng** | Gom được ba pain học tập thành một workflow: xác định mục tiêu → đánh giá hiện tại → nhận diện kỹ năng thiếu → đề xuất roadmap | Domain còn rộng; chưa có competency framework, metric đánh giá phù hợp và baseline; dễ trở thành recommender chung chung |

## 2.4. Scorecard và quyết định hội tụ

Nhóm chấm từ 1–5 theo cùng một bộ tiêu chí. Điểm dùng để làm rõ trade-off và hỗ trợ đồng thuận, không thay thế thảo luận.

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| PolicyMate — đúng điều khoản và hiệu lực | 5 | 5 | 4 | 5 | 4 | 5 | 5 | **33** |
| Giải thích quy định nhất quán | 5 | 4 | 3 | 4 | 3 | 5 | 4 | **28** |
| Roadmap học tập theo khoảng cách kỹ năng | 4 | 4 | 3 | 3 | 4 | 4 | 3 | **25** |

### Giải thích điểm số

- **PolicyMate:** actor và workflow cụ thể nhất; pain thể hiện qua việc phải mở nhiều tài liệu và kiểm tra hiệu lực. Có thể đo bằng cùng một bộ tác vụ tra cứu. Điểm “làm trong lab” là 4 thay vì 5 vì cần dữ liệu văn bản và metadata đủ sạch.
- **Giải thích quy định nhất quán:** impact đáng kể nhưng khó xác định ground truth nếu chưa có chuyên viên nghiệp vụ hoặc đơn vị có thẩm quyền duyệt cách diễn giải.
- **Roadmap học tập:** dễ tạo prototype nhưng domain quá rộng; chất lượng roadmap và “kỹ năng còn thiếu” chưa có chuẩn đo thống nhất.

**Candidate nhóm chọn:** PolicyMate — tra cứu đúng văn bản/quy chế đang có hiệu lực.

### Vì sao chọn

- Bao phủ một workflow thật từ tìm kiếm, kiểm tra hiệu lực đến trích dẫn điều khoản.
- Actor cụ thể: lãnh đạo, nhân viên và giảng viên cần tra cứu để xử lý nghiệp vụ.
- Bottleneck cụ thể: search trả nhiều tài liệu nhưng người dùng vẫn phải mở file, tìm điều khoản và xác định văn bản còn hiệu lực.
- Impact có thể đo: thời gian tra cứu, answer correctness, citation accuracy và version/effectiveness accuracy.
- So sánh rõ được No AI/process fix, Rule, Workflow và Agent.
- Có thể thu hẹp thành pilot trên một loại quy chế, một đơn vị và một bộ câu hỏi nhỏ.

### Vì sao chưa chọn các candidate còn lại

- **Giải thích quy định nhất quán:** được giữ như tác động kỳ vọng dài hạn, chưa đưa vào scope pilot vì AI không được tự diễn giải thay chuyên viên/người có thẩm quyền. Pilot trước hết phải chứng minh tìm đúng nguồn, đúng điều khoản và đúng hiệu lực.
- **Roadmap học tập cá nhân:** pain có thật nhưng chưa xác định một nhóm người học, nghề/kỹ năng đích, competency framework và metric chất lượng đủ rõ trong thời gian lab.

### Challenge đã làm rõ scope

| Challenge | Nhóm làm rõ / điều chỉnh |
|---|---|
| Tìm được đoạn có từ khóa đã được xem là trả lời đúng chưa? | Chưa. Output phải đúng ngữ cảnh, đúng điều/khoản và có citation để người dùng mở nguồn kiểm tra. |
| Citation đúng nhưng văn bản đã hết hiệu lực thì sao? | Vẫn là lỗi nghiêm trọng. Nhóm tách riêng metric citation accuracy và version/effectiveness accuracy. |
| AI có được kết luận cách áp dụng quy định không? | Không. AI chỉ draft dựa trên nguồn; chuyên viên/người có thẩm quyền kiểm tra và quyết định. |
| Nếu metadata văn bản chưa đầy đủ thì có nên xây AI ngay không? | Chưa. Cần process fix và audit dữ liệu trước; đây là lý do quyết định cuối có thể là Not Yet. |
| Có cần Agent tự tìm và tự quyết định không? | Chưa cần. Workflow có các bước cố định và điểm duyệt rõ, nên Workflow an toàn và dễ audit hơn. |

### Cách nhóm xử lý khác biệt quan điểm

Nhóm không chọn bằng cách ưu tiên ý tưởng nghe “AI” nhất. Các candidates được đưa về cùng tiêu chí, gom các pain trùng workflow rồi chấm điểm. Những phần chưa có bằng chứng, như baseline và chất lượng metadata, không được cộng điểm giả mà chuyển thành giả thuyết cần kiểm chứng ở Phase 4. Nhóm thống nhất chọn PolicyMate để đào sâu nhưng chưa mặc định quyết định `Go`.

---

# 3. Phase 4 — Quick Validation + Research

## 3.1. Giả thuyết cần kiểm chứng

| Mã | Giả thuyết | Bằng chứng cần có | Ngưỡng ra quyết định |
|---|---|---|---|
| H1 | Người dùng thật sự mất nhiều thời gian tìm đúng văn bản có hiệu lực | 5–10 tác vụ tra cứu thực tế, ghi thời gian và số file phải mở | Median time đủ lớn để việc giảm 50% có ý nghĩa |
| H2 | Pain chính nằm ở xác định hiệu lực/citation, không chỉ ở search từ khóa | Phỏng vấn 3–5 người và phân loại lỗi của các tác vụ mẫu | Phần lớn người dùng nhắc đến version, hiệu lực hoặc điều khoản |
| H3 | Kho văn bản có thể lập chỉ mục với metadata tối thiểu | Audit một mẫu 30–50 văn bản | Có số hiệu, ngày ban hành, đơn vị, trạng thái và quan hệ sửa đổi hoặc có thể bổ sung |
| H4 | Người dùng chấp nhận AI draft nếu luôn có nguồn để kiểm tra | Prototype test với câu trả lời kèm citation | Người dùng xác minh được nguồn và không hiểu AI là người quyết định |
| H5 | Phân quyền tài liệu có thể được giữ nguyên khi search | Kiểm tra ACL/role trên kho mẫu | Không có kết quả nào vượt quyền trong test |

## 3.2. Kế hoạch quick validation

### Phỏng vấn nhanh 3–5 người

Nên chọn ít nhất một người ở mỗi nhóm: chuyên viên nghiệp vụ, giảng viên và quản lý.

1. Lần gần nhất anh/chị phải tìm một quy định là khi nào?
2. Anh/chị bắt đầu tìm ở đâu và phải mở bao nhiêu tài liệu?
3. Bước khó nhất là tìm file, hiểu điều khoản hay xác định văn bản còn hiệu lực?
4. Tác vụ đó mất khoảng bao lâu?
5. Anh/chị kiểm tra câu trả lời bằng cách nào trước khi sử dụng?
6. Nếu hệ thống đưa câu trả lời kèm citation, điều gì khiến anh/chị không tin hoặc không dùng?
7. Loại văn bản nào anh/chị được phép và không được phép truy cập?

### Benchmark nhỏ

- Chọn 5–10 câu hỏi nghiệp vụ đã có đáp án được chuyên viên xác nhận.
- Ghi lại văn bản nguồn, số hiệu, điều/khoản và phiên bản có hiệu lực.
- Cho người dùng làm theo workflow hiện tại và đo thời gian.
- Chạy prototype trên cùng bộ câu hỏi.
- Chuyên viên chấm correctness, citation accuracy, version/effectiveness accuracy và mức độ phải sửa.

## 3.3. Kết quả validation hiện có

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Interview | Chưa thực hiện | Chưa có | Chưa có | Chờ dữ liệu thật |
| Survey / poll | Chưa thực hiện | Chưa có | Chưa có | Chờ dữ liệu thật |
| Log tác vụ tra cứu | Chưa thu thập | Chưa có baseline | Chưa có | Không tuyên bố đã giảm 50% |
| Mẫu kho văn bản | Chưa audit | Chưa rõ metadata/versioning | Chưa rõ | Giữ quyết định ở mức Not Yet |

## 3.4. Research giải pháp và pattern hiện có

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Google NotebookLM | [Use chat in NotebookLM](https://support.google.com/notebooklm/answer/16179559?hl=en) | Hỏi đáp trên các nguồn người dùng chọn và hiển thị citation dẫn về đoạn nguồn | Prototype nhanh cho pattern grounded Q&A; người dùng mở được context của citation | Không tự giải quyết trạng thái hiệu lực, quan hệ sửa đổi hoặc mô hình phân quyền đặc thù của trường | Citation giúp kiểm tra, nhưng citation đúng file chưa đồng nghĩa văn bản còn hiệu lực |
| Azure AI Search — document-level access | [Document-Level Access Control](https://learn.microsoft.com/en-us/azure/search/search-document-level-access-overview) | Giới hạn kết quả tìm kiếm theo quyền ở cấp tài liệu bằng security filters/ACL/RBAC | Có pattern security trimming và tích hợp danh tính | Một số cơ chế native còn ở preview; ACL stale hoặc cấu hình sai có thể gây rủi ro | Phân quyền phải được kiểm soát ở retrieval layer, không chỉ bằng prompt |
| Azure AI Search — query-time enforcement | [Query-Time ACL and RBAC Enforcement](https://learn.microsoft.com/en-us/azure/search/search-query-access-control-rbac-enforcement) | Lọc kết quả theo user/group tại thời điểm truy vấn | Không trả nội dung không được phép nếu kiểm tra ACL thất bại | Cần đồng bộ quyền và thiết kế fail-closed; có giới hạn theo nguồn dữ liệu | PolicyMate phải fail closed: lỗi phân quyền thì không trả một phần kết quả |
| PowerDMS policy management | [PowerDMS Policy overview](https://www.powerdms.com/hubfs/Executive%20Summary/powerdms-policy-onesheet-2022.pdf?hsLang=en) | Quản lý chính sách tập trung, version control, tracking và search | Cho thấy metadata/version control là năng lực lõi trước AI | Không chứng minh rằng AI có thể tự xác định hiệu lực đúng trong kho dữ liệu chưa chuẩn hóa | Có thể cần policy management/process fix trước khi xây trợ lý AI |

## 3.5. Research benchmark cho target 85% và giảm 50%

### Bằng chứng tham khảo

| Nguồn | Kết quả liên quan | Ý nghĩa với PolicyMate | Giới hạn khi sử dụng |
|---|---|---|---|
| Microsoft Research — [Early Impacts of M365 Copilot](https://www.microsoft.com/en-us/research/publication/early-impacts-of-m365-copilot/) | Thí nghiệm thực địa trên hơn 6.000 lao động tại 56 công ty ghi nhận người dùng Copilot hoàn thành tác vụ tạo tài liệu nhanh hơn 12% | Cho thấy AI có thể tạo hiệu quả thời gian trong knowledge work | Không phải tác vụ tra cứu quy chế; không trực tiếp chứng minh target giảm 50% |
| OpenAI/Zenken — [Enterprise case study](https://openai.com/index/zenken/) | Doanh nghiệp báo cáo tiết kiệm trung bình 30–50% thời gian trên các tác vụ knowledge work | Cho thấy mục tiêu giảm 50% có thể dùng làm stretch target | Case study do doanh nghiệp tự báo cáo; không phải nghiên cứu độc lập và không riêng cho policy search |
| OpenAI/Morgan Stanley — [AI evals in financial services](https://openai.com/index/morgan-stanley/) | Khả năng tiếp cận tài liệu được báo cáo tăng từ 20% lên 80%; hệ thống dùng evaluation dataset, regression test và human review | Hỗ trợ pattern trợ lý tra cứu nội bộ có eval và người thật kiểm tra | Không công bố answer correctness hoặc tỷ lệ giảm thời gian tương ứng với PolicyMate |
| Legal-DC — [Benchmarking RAG for Legal Documents](https://arxiv.org/abs/2603.11772) | Benchmark gồm 480 văn bản và 2.475 cặp hỏi–đáp có tham chiếu cấp điều khoản; kiến trúc giữ cấu trúc điều khoản và reranking cải thiện các metric 1,3–5,6 điểm | Hỗ trợ cách xây ground truth cấp điều/khoản và đánh giá riêng retriever/generator | Dữ liệu luật Trung Quốc, không phải quy chế đại học Việt Nam |
| NIST — [Evaluation of Machine-Generated Reports](https://www.nist.gov/publications/evaluation-machine-generated-reports) | Khuyến nghị đánh giá riêng tính đầy đủ, chính xác và khả năng kiểm chứng; citation phải nối claim với tài liệu nguồn | Hỗ trợ việc tách answer correctness khỏi citation accuracy | Không đề xuất một ngưỡng 85% dùng chung cho mọi domain |
| OfficeQA Pro — [Complex enterprise-document benchmark](https://openai.com/index/databricks/) | Benchmark gồm PDF scan, file cũ và tài liệu dài; kết quả được công bố mới vượt 50% accuracy | Cho thấy parsing/OCR và tài liệu legacy là rủi ro thật; target 85% là tham vọng và cần scope pilot hẹp | Benchmark khác domain và mức độ khó; không dùng làm baseline trực tiếp |

### Cách nhóm sử dụng research

Nhóm **không** dùng các con số bên ngoài để tuyên bố PolicyMate đã đạt kết quả. Research chỉ hỗ trợ:

- xác nhận knowledge retrieval là bài toán có thể tạo tác động về thời gian;
- đặt `giảm ≥50% median time-to-answer` làm **stretch target** cho pilot;
- đặt `answer correctness ≥85%` làm **ngưỡng chấp nhận nội bộ**, không phải benchmark mặc định của thị trường;
- tách riêng `citation accuracy ≥95%`, `version accuracy = 100%` và `access violation = 0`;
- thiết kế benchmark nội bộ có câu hỏi, đáp án và citation do chuyên viên duyệt.

### Lập luận cho target thời gian

Microsoft Research ghi nhận mức cải thiện 12% ở tác vụ tạo tài liệu, trong khi Zenken báo cáo 30–50% trên nhiều tác vụ tri thức và Morgan Stanley ghi nhận khả năng tiếp cận tài liệu tăng đáng kể sau khi triển khai trợ lý nội bộ. Các kết quả khác nhau cho thấy mức tiết kiệm phụ thuộc mạnh vào workflow. Vì PolicyMate tập trung vào bước tìm kiếm và đối chiếu đang làm thủ công, nhóm giữ mục tiêu giảm ít nhất 50% làm stretch target, nhưng chỉ kết luận đạt khi đo trên cùng bộ 5–10 tác vụ trước và sau pilot.

### Lập luận cho target chất lượng

Legal-DC cho thấy đánh giá RAG văn bản pháp lý cần ground truth gắn với điều khoản và đánh giá đồng thời retrieval lẫn generation. NIST cũng nhấn mạnh tính chính xác và khả năng kiểm chứng bằng citation. Tuy nhiên, benchmark OfficeQA Pro cho thấy tài liệu scan, file cũ và tài liệu dài vẫn gây khó cho hệ thống hiện đại. Vì vậy:

- `answer correctness ≥85%` là ngưỡng pilot do nhóm đề xuất, cần chuyên viên chấm;
- `citation accuracy ≥95%` kiểm tra số hiệu, điều/khoản và đoạn nguồn;
- citation đúng nhưng dùng văn bản hết hiệu lực vẫn tính là lỗi;
- `version accuracy = 100%` và `access violation = 0` là gate bắt buộc trong phạm vi pilot.

### Kết luận research

```text
Research hỗ trợ tính khả thi và cách thiết kế metric,
nhưng không thay thế validation trên dữ liệu của trường.

Target 85% và giảm 50% vẫn mang trạng thái:
“mục tiêu cần kiểm chứng”, không phải “kết quả đã đạt”.
```

## 3.6. Research takeaway

```text
PolicyMate không nên được xem là một chatbot đọc toàn bộ kho tài liệu.

Giải pháp hợp lý là một workflow có kiểm soát:
1. quản trị tài liệu và trạng thái hiệu lực bằng metadata/rule;
2. giữ nguyên phân quyền khi retrieval;
3. AI chỉ diễn giải câu hỏi và draft câu trả lời trên các đoạn được phép;
4. luôn trả citation;
5. người dùng/chuyên viên xác minh và chịu trách nhiệm quyết định.
```

Research cũng cho thấy cần tách hai khái niệm:

- **Citation accuracy:** trích dẫn có thật và đúng đoạn nguồn.
- **Answer/effectiveness accuracy:** kết luận nghiệp vụ đúng và văn bản đang có hiệu lực.

Một câu trả lời có citation vẫn có thể sai nếu citation đến từ văn bản cũ.

---

# 4. Phase 5 — Workflow + Problem Statement

## 4.1. Current workflow

```text
CURRENT STATE — baseline chưa đo

[1 Người dùng phát sinh câu hỏi nghiệp vụ]
→ [2 Tự nghĩ từ khóa]
→ [3 Tìm trong thư mục/cổng văn bản hoặc hỏi đồng nghiệp]
→ [4 Mở và đọc nhiều tài liệu gần giống nhau]
→ [5 Kiểm tra số hiệu, ngày ban hành, phạm vi và hiệu lực]  <-- bottleneck
→ [6 Đối chiếu văn bản gốc với văn bản sửa đổi/thay thế]
→ [7 Trích điều khoản và sử dụng để tư vấn/xử lý công việc]
→ [8 Người có thẩm quyền kiểm tra và quyết định]
```

| Bước | Actor | Input | Output | Thời gian/tần suất | Ghi chú |
|---:|---|---|---|---|---|
| 1 | Lãnh đạo/nhân viên/giảng viên | Tình huống nghiệp vụ | Câu hỏi cần tra cứu | Chưa đo | Câu hỏi thường dùng ngôn ngữ nghiệp vụ, không trùng từ trong văn bản |
| 2 | Người tra cứu | Câu hỏi | Bộ từ khóa | Chưa đo | Có thể bỏ sót thuật ngữ pháp lý/hành chính |
| 3 | Người tra cứu/đồng nghiệp | Từ khóa, kinh nghiệm cá nhân | Danh sách file khả dĩ | Chưa đo | Nguồn phân tán, phụ thuộc trí nhớ |
| 4 | Người tra cứu | Nhiều file | Các đoạn có vẻ liên quan | Chưa đo | File khác định dạng, tên gần giống |
| 5 | Người tra cứu/chuyên viên | Số hiệu, ngày, metadata | Văn bản có khả năng còn hiệu lực | Chưa đo | Bottleneck chính |
| 6 | Chuyên viên nghiệp vụ | Văn bản gốc và sửa đổi | Điều khoản áp dụng | Chưa đo | Rủi ro bỏ sót quan hệ thay thế/sửa đổi |
| 7 | Người tra cứu | Điều khoản đã chọn | Câu trả lời/tư vấn | Chưa đo | Có thể trích thiếu context |
| 8 | Người có thẩm quyền | Câu trả lời và nguồn | Quyết định cuối | Theo từng vụ việc | Không thuộc phạm vi tự động hóa |

**Bottleneck chính:** xác định đúng văn bản, đúng phiên bản có hiệu lực và đúng điều/khoản áp dụng. Search từ khóa chỉ giải quyết việc “tìm thấy file”, chưa giải quyết độ tin cậy nghiệp vụ.

## 4.2. Future workflow

```text
FUTURE STATE — mục tiêu cần validation

[1 Người dùng đăng nhập và đặt câu hỏi]
→ [2 Rule kiểm tra vai trò/quyền truy cập]  <-- fail closed
→ [3 Workflow chuẩn hóa câu hỏi và truy xuất tài liệu được phép]
→ [4 Rule lọc metadata: loại văn bản hết hiệu lực/thay thế]
→ [5 AI xếp đoạn liên quan và draft câu trả lời]
→ [6 Hệ thống gắn số hiệu, điều/khoản, phiên bản và link nguồn]
→ [7 Kiểm tra tự động: thiếu citation/xung đột/độ tin cậy thấp?]
    ├─ Có → [Không kết luận; chuyển chuyên viên]
    └─ Không → [Hiển thị draft]
→ [8 Người dùng/chuyên viên mở nguồn, kiểm tra và chỉnh sửa]  <-- human boundary
→ [9 Người có thẩm quyền quyết định]

Fallback:
- Không có nguồn chính thức → không tạo kết luận.
- Không xác định được hiệu lực → hiển thị cảnh báo và chuyển chuyên viên.
- Lỗi ACL/xác thực → không trả nội dung.
- AI draft sai/nhạt → bỏ draft, quay về search + chuyên viên tra cứu.
```

## 4.3. Before/after impact

| Metric | Trước | Sau kỳ vọng | Cách đo / ghi chú |
|---|---:|---:|---|
| Tổng thời gian/tác vụ | Chưa đo | Giảm ≥50% so với baseline | Median của cùng bộ 5–10 tác vụ |
| Answer correctness | Chưa đo | ≥85% | Chuyên viên chấm trên bộ câu hỏi có ground truth |
| Citation accuracy | Chưa đo | ≥95% | Đúng số hiệu, điều/khoản và đoạn nguồn |
| Hiệu lực/version accuracy | Chưa đo | 100% trên pilot | Không chấp nhận dùng nhầm văn bản hết hiệu lực |
| Câu trả lời không có nguồn | Chưa đo | 0 | Hệ thống phải abstain |
| Truy cập vượt quyền | Chưa đo | 0 | Test bằng các role khác nhau |
| Số bước thủ công | 8/8 theo workflow giả định | 2/9 | Người thật vẫn kiểm tra và quyết định |
| Bottleneck chính | Tìm và đối chiếu văn bản | Kiểm tra draft/exception | Bottleneck mới là human boundary có chủ đích |
| Risk mới | Dùng nhầm file thủ công | Hallucination, citation sai, rò quyền, metadata stale | Cần audit và fallback |

## 4.4. Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Lãnh đạo, nhân viên và giảng viên trường đại học cần tra cứu quy định/quy chế để xử lý công việc. |
| **Workflow** | Diễn giải nhu cầu thành từ khóa → tìm trong kho nội bộ/hỏi đồng nghiệp → mở nhiều file → kiểm tra số hiệu và hiệu lực → đối chiếu sửa đổi → trích điều khoản → người có thẩm quyền quyết định. |
| **Bottleneck** | Xác định đúng văn bản, đúng phiên bản có hiệu lực và đúng điều/khoản; tài liệu phân tán, khác định dạng và có thể tồn tại nhiều phiên bản. |
| **Impact** | Mất thời gian tra cứu, trả lời chậm và có nguy cơ viện dẫn nhầm văn bản hoặc điều khoản. Baseline chưa được đo. |
| **Success Metric** | Giảm ≥50% median time-to-answer; answer correctness ≥85%; citation accuracy ≥95%; không dùng nhầm văn bản hết hiệu lực và không truy cập vượt quyền trong pilot. |
| **Boundary** | Chỉ dùng tài liệu chính thức mà người dùng có quyền xem; không tự quyết định hiệu lực khi metadata chưa rõ; không thay chuyên viên hoặc người có thẩm quyền; không trả lời kết luận khi thiếu nguồn. |

---

# 5. Phase 6 — Rule / Workflow / Agent + Decision

## 5.1. Ma trận độ phù hợp với AI

**Ô phù hợp:** độ phức tạp cao, độ mơ hồ trung bình–cao.

**Lý do:**

- Có nhiều bước và nhiều loại dữ liệu: xác thực, phân quyền, retrieval, metadata hiệu lực, văn bản gốc/sửa đổi, citation và review.
- Câu hỏi nghiệp vụ có nhiều cách diễn đạt nên search từ khóa thuần túy chưa đủ.
- Đáp án cuối phải có căn cứ đúng/sai khá rõ theo văn bản, nhưng việc hiểu ý câu hỏi và tổng hợp nhiều đoạn vẫn có độ mơ hồ.
- AI không cần tự quyết định bước tiếp theo ngoài flow đã thiết kế; do đó chưa cần Agent tự trị.

## 5.2. So sánh No AI / Rule / Workflow / Agent

| Mức | Phương án cho PolicyMate | Khi nào đủ | Rủi ro / hạn chế | Chọn? |
|---|---|---|---|---|
| **No AI / process fix** | Gom văn bản về một kho; quy định owner; chuẩn hóa tên file, số hiệu, trạng thái và quan hệ sửa đổi | Cần làm ngay nếu kho dữ liệu đang lộn xộn | Người dùng vẫn phải tự diễn giải câu hỏi và đọc nhiều tài liệu | Bắt buộc làm nền |
| **Rule** | Bộ lọc theo đơn vị, loại văn bản, ngày, trạng thái hiệu lực; exact search; ACL | Đủ cho câu hỏi có từ khóa/số hiệu rõ | Khó xử lý câu hỏi nghiệp vụ diễn đạt tự nhiên và tổng hợp nhiều điều khoản | Dùng cho metadata, hiệu lực và quyền |
| **Workflow** | Authenticate → permission filter → retrieve → filter hiệu lực → AI draft → citation check → human review | Phù hợp khi các bước cố định và AI chỉ hỗ trợ hiểu/tổng hợp ngôn ngữ | Hallucination, citation sai, metadata stale; cần fallback | **Chọn cho pilot** |
| **Agent** | Tự chọn nguồn, gọi nhiều hệ thống, hỏi thêm và tự quyết định bước tiếp theo | Chỉ đáng cân nhắc khi workflow thật có nhiều nhánh động đã được kiểm soát | Permission rộng, khó audit, rủi ro tự chọn sai nguồn hoặc hành động vượt phạm vi | Chưa chọn |

**Mức kiến trúc đề xuất:** Workflow.

**Vì sao chọn:** workflow hiện tại có thể mô tả thành chuỗi bước và checkpoint rõ. Rule phù hợp với quyền truy cập/trạng thái hiệu lực; AI phù hợp với diễn giải câu hỏi và draft câu trả lời; con người kiểm tra trước khi sử dụng.

**Vì sao không chỉ dùng Rule:** rule/search có thể giải phần lớn câu hỏi biết sẵn số hiệu hoặc từ khóa, nhưng chưa xử lý tốt câu hỏi nghiệp vụ diễn đạt tự nhiên và việc tổng hợp nhiều điều khoản liên quan.

**Vì sao chưa dùng Agent:** không có nhu cầu đã kiểm chứng để AI tự lập kế hoạch, tự thay đổi workflow hoặc tự hành động. Agent làm tăng quyền truy cập và khó audit mà chưa chứng minh thêm giá trị.

## 5.3. Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Lãnh đạo, nhân viên và giảng viên trường đại học có quyền truy cập khác nhau, cần tra cứu văn bản/quy chế để xử lý công việc. |
| **Workflow** | Phát sinh câu hỏi → tìm/hỏi đồng nghiệp → mở nhiều file → kiểm tra số hiệu và hiệu lực → đối chiếu sửa đổi → trích điều khoản → kiểm tra → quyết định. |
| **Bottleneck** | Bước xác định đúng văn bản, phiên bản có hiệu lực và điều/khoản áp dụng; search từ khóa không biểu diễn đủ câu hỏi nghiệp vụ và quan hệ giữa các phiên bản. |
| **Impact** | Tra cứu chậm, phụ thuộc kinh nghiệm cá nhân và có nguy cơ viện dẫn nhầm nguồn. Baseline vẫn cần đo bằng tác vụ thực tế. |
| **Success Metric** | Giảm ≥50% median time-to-answer; answer correctness ≥85%; citation accuracy ≥95%; 100% pilot không dùng nhầm văn bản hết hiệu lực; 0 kết quả vượt quyền; 0 kết luận không có nguồn. |
| **Boundary** | Chỉ retrieval trên tài liệu chính thức được phép; không tự xác lập hiệu lực khi thiếu metadata; không thay chuyên viên hoặc người có thẩm quyền; không tự thực hiện quyết định; fail closed khi lỗi quyền. |
| **AI intervention point** | Sau khi xác thực/phân quyền và retrieval các tài liệu hợp lệ, trước bước người dùng/chuyên viên kiểm tra câu trả lời. |
| **Mức chọn** | Workflow: process fix + rule/metadata + retrieval/AI draft + human review. |
| **Rủi ro & người thật kiểm tra** | Hallucination, bỏ sót sửa đổi, citation đúng đoạn nhưng sai phiên bản, rò tài liệu. Chuyên viên nghiệp vụ kiểm tra nội dung/hiệu lực; quản trị hệ thống kiểm tra ACL; người có thẩm quyền quyết định cuối. |

## 5.4. Final decision

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | Yes | Đã xác định actor, chuỗi bước và bottleneck |
| Baseline và success metric đã đo được chưa? | Not Yet | Có target nhưng chưa có log hiện trạng |
| Có data/input đủ dùng chưa? | Not Yet | Chưa audit kho mẫu, OCR, metadata, hiệu lực và ACL |
| Nếu AI sai, hậu quả có chấp nhận được không? | Not Yet | Chỉ chấp nhận khi giới hạn ở draft, có citation, abstain và human review |
| Có người review/owner vận hành không? | Not Yet | Chưa ghi nhận chuyên viên/đơn vị owner cụ thể |
| Có cách non-AI đơn giản hơn không? | Yes | Chuẩn hóa kho, metadata, search và quy trình quản trị văn bản cần được làm trước/song song |

**Decision hiện tại:**

```text
NOT YET — có tiềm năng Go với pilot nhỏ sau khi hoàn tất validation và data readiness.
```

**Lý do:**

- Problem, actor, workflow và boundary đã đủ rõ để tiếp tục nghiên cứu.
- AI có điểm can thiệp hợp lý ở bước hiểu câu hỏi và draft có citation.
- Tuy nhiên, chưa có baseline, ground truth, audit metadata/hiệu lực, kiểm tra ACL hoặc owner chịu trách nhiệm.
- Chọn Go ngay lúc này sẽ biến target 85% và giảm 50% thành tuyên bố không có bằng chứng.

**Pilot nhỏ nhất sau khi đủ điều kiện:**

1. Chọn một loại quy chế không mật và một đơn vị nghiệp vụ.
2. Chuẩn hóa 30–50 văn bản, bao gồm metadata hiệu lực và quan hệ sửa đổi.
3. Chọn 10–20 câu hỏi đã có đáp án do chuyên viên xác nhận.
4. Chạy workflow bán thủ công, không kết nối toàn kho và không cho AI hành động.
5. Hiển thị mọi citation và yêu cầu chuyên viên duyệt.
6. So sánh với workflow hiện tại về thời gian, correctness, citation và số lỗi version.

**Điều kiện chuyển từ Not Yet sang Go:**

- Có owner nghiệp vụ và owner dữ liệu.
- Kho pilot có metadata/hiệu lực đủ tin cậy.
- ACL test không có trường hợp vượt quyền.
- Bộ ground truth được chuyên viên phê duyệt.
- Baseline cho thấy pain đủ lớn.
- Prototype đạt correctness ≥85%, citation accuracy ≥95%, không dùng nhầm văn bản hết hiệu lực và giảm ≥50% median time.

**Exit / rollback:**

- Có truy cập vượt quyền hoặc lộ tài liệu → dừng pilot ngay.
- Có câu trả lời không nguồn hoặc dùng nhầm văn bản hết hiệu lực → tắt AI answer, quay về search/filter.
- Người dùng phải viết lại phần lớn câu trả lời hoặc không tiết kiệm đủ thời gian → hạ về process fix + rule/search.

---

AI được dùng để:

- hệ thống hóa candidate PolicyMate theo đúng các phase trong worksheet;
- phản biện metric, boundary và rủi ro;
- research pattern giải pháp hiện có từ tài liệu chính thức;
- chuyển workflow thành dạng dễ kiểm tra.

AI không có quyền:

- tạo log pitch, phỏng vấn hoặc phiếu chấm giả;
- gán phát biểu/đóng góp cho thành viên khi không có bằng chứng;
- biến target thành kết quả đã đo;
- quyết định thay nhóm.

---

# 7. Validation Pack — hoàn thiện bằng dữ liệu thật

> Phần này biến các mục còn thiếu thành biểu mẫu thực thi. Người phụ trách phải điền kết quả thật và đính kèm bằng chứng đã ẩn dữ liệu nhạy cảm. Không điền số liệu ước đoán.

## 7.1. Phân công validation và output

| Đầu việc | Người chịu trách nhiệm chính | Người kiểm tra chéo | Output cần bàn giao |
|---|---|---|---|
| Biên bản pitch/challenge | Nguyễn Thị Xuân Mai | Lưu Quang Nhật | Log hội tụ có tên người phát biểu và quyết định |
| Phỏng vấn 3–5 người dùng | Đoàn Minh Hiếu | Nguyễn Thị Xuân Mai | Notes đã ẩn danh + bảng insight |
| Survey 5–10 người | Kim Mạnh Hưng | Đoàn Minh Hiếu | Ảnh kết quả + file raw data đã ẩn danh |
| Đo baseline 5–10 tác vụ | Kim Mạnh Hưng | Ngô Khánh Trượng | Bảng thời gian, số file mở và kết quả đúng/sai |
| Audit 30–50 văn bản | Trần Đoàn Hưng | Đinh Lê Quỳnh Phương | Bảng metadata, hiệu lực, OCR và quan hệ sửa đổi |
| Research giải pháp | Lê Tuấn Hiệp | Nguyễn Ngọc Sơn | Link nguồn + nhận xét giải pháp/khoảng trống |
| Current Workflow | Ngô Khánh Trượng | Kim Mạnh Hưng | Workflow có thời gian thật ở từng bước |
| Future Workflow/pilot | Cao Hữu Phúc | Nguyễn Ngọc Sơn | Workflow, fallback, rollback và permission test |
| Metric + Problem Statement | Đinh Lê Quỳnh Phương | Phùng Văn Linh | Baseline, target, cách đo và PS v1 cuối |
| Risk/boundary/QA | Nguyễn Ngọc Sơn | Cao Hữu Phúc | Checklist citation, ACL, hiệu lực và rubric |
| Quyết định cuối | Phùng Văn Linh | Cả nhóm | Biên bản Go/Not Yet/No-Go và lý do |

## 7.2. Phiếu phỏng vấn nhanh

### Câu hỏi dùng thống nhất

1. Lần gần nhất anh/chị phải tìm một văn bản hoặc quy chế là khi nào?
2. Anh/chị tìm ở đâu và thực hiện theo những bước nào?
3. Anh/chị mất bao lâu và phải mở khoảng bao nhiêu tài liệu?
4. Bước khó nhất là tìm file, tìm điều khoản, kiểm tra hiệu lực hay hiểu cách áp dụng?
5. Anh/chị đã từng gặp văn bản cũ, văn bản thay thế hoặc hai nguồn mâu thuẫn chưa?
6. Anh/chị kiểm tra câu trả lời bằng cách nào trước khi sử dụng?
7. Nếu hệ thống trả lời kèm số hiệu, điều/khoản và link nguồn, điều gì khiến anh/chị vẫn không tin?
8. Loại tài liệu nào anh/chị được phép hoặc không được phép truy cập?
9. Nếu cải thiện workflow, thay đổi nào có giá trị nhất?

### Bảng ghi kết quả

| Người tham gia ẩn danh | Vai trò | Lần gần nhất | Workflow hiện tại | Thời gian | Số tài liệu mở | Pain lớn nhất | Workaround | Tín hiệu xác nhận/phản bác |
|---|---|---|---|---:|---:|---|---|---|
| P01 | | | | | | | | |
| P02 | | | | | | | | |
| P03 | | | | | | | | |
| P04 | | | | | | | | |
| P05 | | | | | | | | |

### Tổng hợp insight sau phỏng vấn

| Câu hỏi | Kết luận từ dữ liệu thật |
|---|---|
| Bao nhiêu người xác nhận pain? | |
| Bước được nhắc là khó nhất? | |
| Median thời gian tự khai báo? | |
| Tín hiệu phản bác mạnh nhất? | |
| Nhóm phải sửa actor/scope/bottleneck thế nào? | |

## 7.3. Micro-survey 5–10 người

### Nội dung survey

1. Vai trò của bạn: lãnh đạo / nhân viên / giảng viên / khác.
2. Bạn tra cứu văn bản/quy chế bao nhiêu lần: hằng ngày / hằng tuần / hằng tháng / hiếm khi?
3. Lần gần nhất mất khoảng bao lâu: `<5`, `5–15`, `16–30`, `31–60`, `>60` phút?
4. Bước khó nhất: tìm file / tìm đúng điều khoản / kiểm tra hiệu lực / hiểu cách áp dụng / kiểm tra quyền?
5. Bạn từng gặp văn bản cũ hoặc văn bản đã bị thay thế chưa: có / không / không chắc?
6. Bạn có phải hỏi lại đồng nghiệp hoặc chuyên viên không: thường xuyên / đôi khi / hiếm khi / không?
7. Mức độ đáng giải quyết của vấn đề: 1–5.
8. Bạn có dùng câu trả lời AI nếu không có citation không: có / không?
9. Bạn muốn citation hiển thị thông tin nào: số hiệu / điều-khoản / ngày hiệu lực / link file / tất cả?
10. Ý kiến hoặc tình huống cụ thể khác.

### Bảng tổng hợp survey

| Metric survey | Kết quả thật |
|---|---:|
| Tổng số người trả lời | |
| Tỷ lệ gặp vấn đề hằng tuần trở lên | |
| Tỷ lệ từng gặp văn bản cũ/thay thế | |
| Tỷ lệ phải hỏi lại người khác | |
| Điểm đáng giải quyết trung bình | |
| Tỷ lệ không chấp nhận câu trả lời thiếu citation | |

## 7.4. Bảng đo baseline tác vụ tra cứu

### Quy tắc đo

- Dùng 5–10 câu hỏi nghiệp vụ có đáp án và nguồn được chuyên viên xác nhận.
- Bắt đầu tính giờ từ lúc người dùng đọc câu hỏi.
- Dừng khi người dùng đưa ra câu trả lời cùng văn bản và điều/khoản nguồn.
- Không thay đổi câu hỏi giữa phép đo hiện trạng và pilot.
- Ghi cả lần không tìm được hoặc chọn sai nguồn.

| Task ID | Câu hỏi rút gọn | Người thực hiện | Thời gian hiện tại (phút) | Số nguồn đã tìm | Số file mở | Tìm đúng điều/khoản? | Đúng phiên bản hiệu lực? | Phải hỏi người khác? |
|---|---|---|---:|---:|---:|---|---|---|
| T01 | | | | | | | | |
| T02 | | | | | | | | |
| T03 | | | | | | | | |
| T04 | | | | | | | | |
| T05 | | | | | | | | |
| T06 | | | | | | | | |
| T07 | | | | | | | | |
| T08 | | | | | | | | |
| T09 | | | | | | | | |
| T10 | | | | | | | | |

### Baseline tổng hợp

| Metric | Công thức | Kết quả thật |
|---|---|---:|
| Median time-to-answer | Trung vị cột thời gian | |
| Tỷ lệ tìm đúng điều/khoản | Task đúng / tổng task | |
| Version accuracy | Task đúng phiên bản / tổng task | |
| Số file mở trung vị | Trung vị số file mở | |
| Tỷ lệ cần hỏi người khác | Task phải hỏi / tổng task | |

## 7.5. Audit dữ liệu 30–50 văn bản

### Field tối thiểu cần kiểm tra

| Field | Ý nghĩa | Điều kiện đạt |
|---|---|---|
| Document ID | Định danh duy nhất | Không trùng, không trống |
| Số hiệu | Số/ký hiệu văn bản | Có thể search/filter |
| Tên văn bản | Tiêu đề chính thức | Khớp nội dung |
| Đơn vị ban hành | Owner của văn bản | Có giá trị chuẩn hóa |
| Ngày ban hành | Ngày phát hành | Parse được |
| Ngày hiệu lực | Thời điểm bắt đầu áp dụng | Có hoặc ghi rõ chưa xác định |
| Ngày hết hiệu lực | Thời điểm ngừng áp dụng | Có hoặc ghi rõ còn hiệu lực |
| Trạng thái | Còn hiệu lực/hết hiệu lực/một phần/chưa rõ | Bắt buộc |
| Văn bản thay thế/sửa đổi | Quan hệ với phiên bản khác | Link được tới Document ID |
| Phạm vi áp dụng | Đơn vị/đối tượng | Có thể filter |
| Quyền truy cập | User/group/role được xem | Không để trống |
| Chất lượng OCR | Nội dung trích xuất đọc được | Không mất số hiệu/điều/khoản |

### Bảng audit mẫu

| Doc ID | Số hiệu | Metadata đủ? | Hiệu lực rõ? | Quan hệ sửa đổi rõ? | ACL rõ? | OCR đạt? | Lỗi chính | Hành động sửa |
|---|---|---|---|---|---|---|---|---|
| D001 | | | | | | | | |
| D002 | | | | | | | | |
| D003 | | | | | | | | |
| … | | | | | | | | |

### Tổng hợp data readiness

| Metric | Ngưỡng pilot đề xuất | Kết quả thật |
|---|---:|---:|
| Văn bản đủ metadata bắt buộc | ≥95% | |
| Văn bản xác định được trạng thái hiệu lực | 100% | |
| Quan hệ sửa đổi/thay thế đúng | 100% trên tập pilot | |
| Văn bản có ACL rõ | 100% | |
| Văn bản OCR đạt yêu cầu | ≥95% | |

Nếu trạng thái hiệu lực hoặc ACL chưa đạt 100%, không dùng tài liệu đó trong pilot.

## 7.6. Ground-truth và bảng chấm prototype

| Task ID | Đáp án chuẩn do chuyên viên duyệt | Citation chuẩn | Phiên bản chuẩn | Thời gian hiện tại | Thời gian pilot | AI đúng nội dung? | Citation đúng? | Đúng hiệu lực? | Mức chỉnh sửa |
|---|---|---|---|---:|---:|---|---|---|---|
| T01 | | | | | | | | | |
| T02 | | | | | | | | | |
| T03 | | | | | | | | | |
| T04 | | | | | | | | | |
| T05 | | | | | | | | | |
| T06 | | | | | | | | | |
| T07 | | | | | | | | | |
| T08 | | | | | | | | | |
| T09 | | | | | | | | | |
| T10 | | | | | | | | | |

### Công thức metric

```text
Time reduction (%) =
  (Median time hiện tại - Median time pilot)
  / Median time hiện tại × 100

Answer correctness (%) =
  Số câu được chuyên viên chấm đúng / Tổng số câu × 100

Citation accuracy (%) =
  Số citation đúng số hiệu + điều/khoản + đoạn nguồn
  / Tổng số citation × 100

Version accuracy (%) =
  Số câu dùng đúng phiên bản có hiệu lực / Tổng số câu × 100

Access violation count =
  Số tài liệu vượt quyền xuất hiện trong retrieval hoặc câu trả lời
```

## 7.7. Permission test

| Test ID | Role giả lập | Tài liệu được phép | Tài liệu không được phép | Kết quả retrieval | Có lộ nội dung? | Pass/Fail |
|---|---|---|---|---|---|---|
| ACL-01 | Giảng viên | | | | | |
| ACL-02 | Nhân viên phòng ban A | | | | | |
| ACL-03 | Nhân viên phòng ban B | | | | | |
| ACL-04 | Lãnh đạo | | | | | |
| ACL-05 | Người không đăng nhập | Không có | Tất cả tài liệu nội bộ | | | |

Quy tắc: có một test lộ tài liệu vượt quyền thì dừng pilot, không lấy điểm trung bình để bỏ qua lỗi.

## 7.8. Kế hoạch đóng góp cá nhân

> Đây là kế hoạch phân công, chưa phải log xác nhận công việc đã hoàn thành. Sau khi thực hiện, thư ký nhóm cập nhật trạng thái và gắn link/ảnh/file bằng chứng thật.

| Thành viên | Hoạt động được giao | Artifact/bằng chứng dự kiến | Challenge hoặc quyết định phụ trách | Ảnh hưởng mong đợi đến report cuối |
|---|---|---|---|---|
| Nguyễn Thị Xuân Mai | Ghi biên bản pitch, challenge, disagreement và kết luận của từng phase; quản lý danh sách evidence | Biên bản họp, ảnh bảng thảo luận, evidence manifest có link và trạng thái | Kiểm tra mỗi kết luận trong report có bằng chứng hoặc được ghi rõ là giả thuyết chưa kiểm chứng hay chưa | Report có khả năng truy vết, không gán nhầm đóng góp và không biến kế hoạch thành kết quả thật |
| Lưu Quang Nhật | Tổng hợp 11 candidates, gom cluster, điều phối shortlist và tính scorecard | Bảng candidates, cluster, shortlist, scorecard và ghi chú lý do cho từng điểm | Challenge việc nhóm chọn theo cảm tính hoặc vì ý tưởng nghe có vẻ “AI”; yêu cầu dùng cùng tiêu chí cho mọi candidate | Lập luận hội tụ minh bạch và giải thích được vì sao PolicyMate được chọn |
| Đoàn Minh Hiếu | Chuẩn bị và thực hiện 3–5 phỏng vấn với lãnh đạo, nhân viên hoặc giảng viên | Interview notes đã ẩn danh, bảng insight và trích ý được người tham gia cho phép | Kiểm tra pain lớn nhất thực sự là search, hiệu lực, citation hay cách diễn giải; tìm cả tín hiệu phản bác | Actor, bottleneck và scope được sửa theo trải nghiệm người dùng thật |
| Kim Mạnh Hưng | Thực hiện survey 5–10 người và đo baseline trên 5–10 tác vụ tra cứu | Ảnh kết quả survey, raw data ẩn danh và bảng baseline thời gian/số file mở | Challenge target “giảm 50%” bằng baseline thật; kiểm tra pain có xảy ra đủ thường xuyên để đáng giải quyết không | Metric có hiện trạng, target và cách đo; quyết định không dựa trên con số ước đoán |
| Trần Đoàn Hưng | Audit 30–50 văn bản về metadata, OCR, trạng thái hiệu lực và quan hệ sửa đổi/thay thế | Data-audit sheet, danh sách lỗi dữ liệu và đề xuất process fix | Kiểm tra AI có thể tìm đúng khi dữ liệu nguồn chưa sạch không; xác định tài liệu nào phải loại khỏi pilot | Làm rõ data readiness, giới hạn pilot và điều kiện chuyển từ Not Yet sang Go |
| Lê Tuấn Hiệp | Research ít nhất 3 giải pháp/pattern tương tự và kiểm tra nguồn chính thức | Research notes có hyperlink, bảng so sánh điểm mạnh, khoảng trống và bài học | Challenge giả định phải tự xây Agent; kiểm tra tool/process hiện có đã giải được bao nhiêu phần trăm workflow | So sánh No AI/Rule/Workflow/Agent có cơ sở và tránh solution-first |
| Ngô Khánh Trượng | Vẽ Current Workflow chi tiết, bổ sung actor, input/output, handoff và thời gian thật sau validation | Sơ đồ current workflow và bảng thời gian từng bước | Kiểm tra bottleneck có thật nằm ở search/kiểm tra hiệu lực hay ở quy trình quản trị tài liệu | Workflow hiện trạng và bottleneck nhất quán với evidence, metric và Problem Statement |
| Phùng Văn Linh | Điều phối tiến độ, tổ chức buổi đồng thuận, xử lý disagreement và làm decision owner | Biên bản quyết định, danh sách việc còn thiếu, xác nhận cuối của nhóm | Buộc nhóm trả lời các gate Go/Not Yet/No-Go; không cho chuyển sang Go khi thiếu baseline, owner hoặc ACL test | Quyết định cuối rõ trách nhiệm, có lý do và được cả nhóm xác nhận |
| Cao Hữu Phúc | Thiết kế Future Workflow, prototype plan, human review, fallback và rollback | Sơ đồ future workflow, pilot plan và bảng kiểm thử permission/fallback | Challenge nhu cầu dùng Agent; xác định AI sai thì ai phát hiện, hệ thống dừng ở đâu và quay về phương án nào | Giải pháp được giới hạn ở Workflow an toàn, có điểm kiểm soát và phương án quay về |
| Đinh Lê Quỳnh Phương | Hoàn thiện Problem Statement v0/v1, chuẩn hóa baseline, target, công thức metric và ground truth | PS v0/v1, metric sheet và bộ câu hỏi/citation chuẩn được chuyên viên duyệt | Kiểm tra các metric 85%, 95%, 100% và giảm 50% có đo được, có owner và có mẫu số rõ hay chưa | Problem Statement đủ actor, workflow, bottleneck, impact, metric và boundary |
| Nguyễn Ngọc Sơn | Rà soát risk, boundary, citation, ACL, audit log và toàn bộ report theo rubric | Risk register, permission-test result, QA checklist và danh sách lỗi cần sửa | Challenge các trường hợp citation đúng nhưng văn bản hết hiệu lực, retrieval vượt quyền hoặc AI trả lời khi thiếu nguồn | Report thể hiện rõ giới hạn AI, fail-closed, human accountability và điều kiện dừng pilot |

## 7.9. Evidence manifest

| Evidence ID | File đề xuất | Nội dung | Owner | Trạng thái |
|---|---|---|---|---|
| E01 | `02-group-problem-statement-interview-notes.md` | Notes 3–5 phỏng vấn đã ẩn danh | Đoàn Minh Hiếu | Chưa có |
| E02 | `02-group-problem-statement-survey.png` | Ảnh kết quả survey | Kim Mạnh Hưng | Chưa có |
| E03 | `02-group-problem-statement-baseline.csv` | Log 5–10 tác vụ hiện trạng | Kim Mạnh Hưng | Chưa có |
| E04 | `02-group-problem-statement-data-audit.csv` | Audit 30–50 văn bản | Trần Đoàn Hưng | Chưa có |
| E05 | `02-group-problem-statement-ground-truth.md` | Đáp án/citation do chuyên viên duyệt | Đinh Lê Quỳnh Phương | Chưa có |
| E06 | `02-group-problem-statement-permission-test.md` | Kết quả kiểm thử ACL | Nguyễn Ngọc Sơn | Chưa có |
| E07 | `02-group-problem-statement-contribution-log.md` | Đóng góp thật của thành viên | Nguyễn Thị Xuân Mai | Chưa có |

## 7.10. Gate ra quyết định cuối

| Gate | Điều kiện Go | Kết quả thật | Pass/Fail |
|---|---|---|---|
| Pain validation | ≥60% người được hỏi xác nhận pain đáng giải quyết | | |
| Baseline | Có ít nhất 5 tác vụ đo được theo cùng quy tắc | | |
| Data readiness | Hiệu lực và ACL đạt 100% trên tập pilot | | |
| Answer correctness | ≥85% | | |
| Citation accuracy | ≥95% | | |
| Version accuracy | 100% trên pilot | | |
| Time reduction | ≥50% median time | | |
| Access safety | 0 kết quả vượt quyền | | |
| Human owner | Có owner nghiệp vụ và owner dữ liệu | | |
