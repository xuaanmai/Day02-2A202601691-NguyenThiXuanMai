# Group Report — Day 02

## 0. Thành viên nhóm

> Danh sách chỉ giữ họ tên, mã học viên và đầu việc cần thiết cho bài lab; không đưa số điện thoại hoặc thông tin liên hệ cá nhân vào report.

| STT | Họ và tên | Mã học viên | Vai trò và đầu việc phụ trách |
|---:|---|---|---|
| 1 | Nguyễn Thị Xuân Mai | 2A202601691 | **Thư ký nhóm:** ghi biên bản pitch/challenge, tổng hợp candidates và lưu bằng chứng thảo luận |
| 2 | Lưu Quang Nhật | 2A202601920 | **Group Convergence:** gom cluster, lập shortlist và tổng hợp scorecard Phase 3 |
| 3 | Đoàn Minh Hiếu | 2A202601733 | **Phỏng vấn người dùng:** chuẩn bị câu hỏi, thực hiện phỏng vấn và tổng hợp tín hiệu xác nhận/phản bác |
| 4 | Kim Mạnh Hưng | 2A202601679 | **Survey và baseline:** triển khai khảo sát, thu log tác vụ và tính thời gian tra cứu hiện tại |
| 5 | Trần Doãn Hưng | 2A202601143 | **Audit dữ liệu văn bản:** kiểm tra metadata, phiên bản, hiệu lực và quan hệ sửa đổi/thay thế |
| 6 | Lê Tuấn Hiệp | 2A202601667 | **Research giải pháp:** tìm công cụ/pattern tương tự, kiểm nguồn và rút ra bài học cho nhóm |
| 7 | Ngô Khánh Trượng | 2A202601477 | **Current Workflow:** mô tả actor, input/output, handoff, thời gian và bottleneck hiện tại |
| 8 | Phùng Văn Linh | 2A202601992 | **Nhóm trưởng/Decision owner:** điều phối tiến độ, xử lý bất đồng, dẫn thảo luận và chốt quyết định nhóm |
| 9 | Cao Hữu Phúc | 2A202601283 | **Future Workflow:** thiết kế điểm can thiệp Rule/AI, human review, fallback và rollback |
| 10 | Đinh Lê Quỳnh Phương | 2A202601865 | **Problem Statement và Metrics:** hoàn thiện v0/v1, baseline, target và cách đo |
| 11 | Nguyễn Ngọc Sơn | 2A202601948 | **Risk, Boundary và QA:** kiểm tra phân quyền, citation, giới hạn AI và rà report theo rubric |

## 1. Trạng thái bằng chứng

Nhóm đã chốt candidate:



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
| 5 | Trần Doãn Hưng | Người học không biết nên bắt đầu học từ đâu | Người mới học một lĩnh vực hoặc kỹ năng | Không biết đánh giá điểm xuất phát và chọn nội dung ưu tiên | Pain gần gũi; cần xác định domain học tập cụ thể |
| 6 | Lê Tuấn Hiệp | Người học không biết mình còn thiếu kỹ năng nào | Sinh viên và người đi làm muốn phát triển năng lực | Khái niệm “kỹ năng còn thiếu” mơ hồ nếu không có chuẩn năng lực đích | Tác động rộng nhưng actor, chuẩn đánh giá và metric chưa đủ chặt |
| 7 | Ngô Khánh Trượng | Văn bản nội bộ nằm rải rác ở nhiều thư mục và định dạng nên khó xác định đâu là nguồn chính thức | Nhân viên, giảng viên và người quản trị văn bản | Phải tìm qua nhiều nguồn, tên file không thống nhất và có tài liệu trùng lặp | Pain xảy ra trước cả bước AI; cần chuẩn hóa kho và metadata |
| 8 | Phùng Văn Linh | Kết quả tra cứu không kèm số hiệu, điều/khoản và đoạn nguồn để người dùng kiểm tra | Người sử dụng câu trả lời để xử lý nghiệp vụ hoặc ra quyết định | Phải tìm lại tài liệu gốc; khó biết câu trả lời dựa trên căn cứ nào | Citation là boundary bắt buộc và có metric rõ |
| 9 | Cao Hữu Phúc | Công cụ tìm kiếm có thể trả về tài liệu mà người dùng không có thẩm quyền xem | Người dùng có các vai trò và phạm vi truy cập khác nhau | Quyền của tài liệu gốc không được giữ nguyên trong lớp tìm kiếm/trợ lý | Rủi ro cao; cần permission filter và kiểm thử truy cập vượt quyền |
| 10 | Đinh Lê Quỳnh Phương | Văn bản scan hoặc khác định dạng khiến nội dung và metadata được trích xuất không đầy đủ | Người quản trị kho và người tra cứu | OCR sai, mất số hiệu/điều khoản hoặc chia đoạn không đúng làm retrieval sai | Cần audit chất lượng dữ liệu trước khi đặt target AI |
| 11 | Nguyễn Ngọc Sơn | Không có log để truy vết người dùng đã nhận câu trả lời nào và dựa trên phiên bản văn bản nào | Quản trị hệ thống, chuyên viên nghiệp vụ và người kiểm tra | Khó điều tra khi có citation sai, văn bản đổi hiệu lực hoặc phát sinh khiếu nại | Audit log quan trọng cho vận hành nhưng cần bảo vệ dữ liệu nhạy cảm |

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

