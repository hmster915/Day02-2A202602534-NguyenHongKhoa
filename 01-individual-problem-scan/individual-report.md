# 01 — Individual Problem Scan

## Thông tin cá nhân

- Họ và tên: Nguyễn Hồng Khoa
- Mã học viên: 2A202602534
- Vai trò / bối cảnh: Software Engineer, đồng thời là sinh viên tự quản lý lịch học và công việc.
- Công việc hằng tuần: học tập; làm project/code; họp và xử lý task; nghỉ ngơi/cá nhân.

---

## Phase 1 — Scan 5+ problems

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật / baseline cần đo |
|---|---|---|---|---|
| 1 | Tốn thời gian / Lặp lại | Khi kế hoạch trong ngày bị gián đoạn bởi cuộc họp, task overrun hoặc việc khẩn, người dùng phải tự xem lại và xếp lại toàn bộ task còn lại. | Sinh viên, knowledge workers | Baseline cần đo qua 5–7 ngày: thời gian re-plan mỗi lần, số lần disruption/tuần và số task bị rollover. Mục tiêu giả định là khoảng 15 phút/lần và 5 lần/tuần; chưa phải số đo đã xác minh. |
| 2 | AI có thể tốt hơn / Tốn thời gian | Khi nhiều deadline cùng lúc, người dùng khó quyết định task nào nên làm trước. | Người quản lý nhiều môn/task/dự án | Theo dõi 10–20 quyết định ưu tiên: thời gian chọn thứ tự, số lần đổi priority và số task quan trọng hoàn thành đúng hạn. |
| 3 | Lặp lại / Tốn thời gian | Estimated effort thường thấp hơn actual effort, làm các task sau bị lệch lịch. | Sinh viên và knowledge workers | Ghi planned vs actual cho ít nhất 20 task; theo dõi % task overrun và số phút lệch trung bình. |
| 4 | AI có thể tốt hơn | Người dùng ưu tiên theo cảm tính, chưa cân nhắc đồng thời deadline, importance, effort, dependency, workload và energy. | Người tự quản lý workload | Với 10 task, ghi lại priority trước/sau khi xem đủ trường; đo số task phải đổi thứ tự và lý do đổi. |
| 5 | Pain từ người khác / Lặp lại | Task chưa hoàn thành bị chuyển sang ngày sau, khiến workload tích tụ và kế hoạch tiếp tục quá tải. | Sinh viên, nhân viên văn phòng | Theo dõi 7 ngày: số task rollover/ngày, số task rollover từ 2 ngày trở lên và tỷ lệ task quan trọng bị ảnh hưởng. |
| 6 | Tốn thời gian | Khi năng lượng hoặc sức khỏe thay đổi, người dùng không biết nên giảm cường độ hay đổi loại task nào. | Người làm việc trí óc, người học sau giờ làm | Check-in energy 1–5 trước và sau phiên làm việc; so sánh với completion rate và số lần bỏ kế hoạch. |
| 7 | Pain từ người khác | Việc mới phát sinh chen vào lịch nhưng không có cách đánh đổi minh bạch với task cũ. | Người nhận nhiều request từ team/giảng viên | Ghi số request chen ngang, thời gian xử lý và task bị đẩy ra; kiểm tra người dùng có hiểu vì sao lịch đổi không. |
| 8 | AI có thể tốt hơn / Lặp lại | Người dùng phải lập lại lịch nhiều lần nhưng không có lịch sử để so sánh recommendation nào hiệu quả. | Người dùng hệ thống planning | Lưu mỗi lần suggestion: thời gian tạo, accept/edit/reject, task rollover và perceived workload 1–5. |

### AI đã dùng ở Phase 1

- Prompt đã hỏi: “Từ bối cảnh sinh viên và knowledge worker phải quản lý nhiều task, deadline, disruption và thay đổi năng lượng, hãy liệt kê pain points quan sát được trước khi đề xuất solution.”
- Ý dùng được: re-planning sau disruption; effort estimate sai; deadline pressure; dependency; energy/focus; task rollover; workload tăng do việc mới.
- Ý bỏ vì chưa phải pain đã chứng minh: “AI tự quản lý toàn bộ cuộc sống”, “tự động hủy mọi task”, “dùng Agent cho mọi quyết định”, và các con số không có log/interview hỗ trợ.

### Self-check Phase 1

- [x] Có 8 problems, mỗi dòng có actor và cách đo.
- [x] Dùng đủ 4 lăng kính.
- [x] Phân biệt baseline giả định với evidence cần thu thập.

---

## Phase 2 — Top 3 Problem Cards

### 2.1. Chọn top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Re-plan phần ngày còn lại sau disruption | Actor rõ; workflow có thể quan sát từ plan đến continue; trực tiếp khớp core problem và MVP. | Baseline re-plan thực tế và mức chấp nhận recommendation cần đo. |
| 2 | Ưu tiên task khi có nhiều deadline | Có thể dùng scoring, Eisenhower và deadline pressure; metric completion dễ theo dõi. | Weighted score nào phản ánh đúng cách người dùng quyết định; dependency có làm score sai không. |
| 3 | Ước lượng effort sai gây schedule drift | Có dữ liệu planned/actual rõ; là input quan trọng cho engine. | Sai lệch đến từ estimate hay disruption; hệ thống có đủ dữ liệu để dự đoán effort chính xác hơn không. |

### 2.2. Problem Card #1 — Adaptive re-planning sau disruption

```text
Problem 1 câu:
Khi kế hoạch trong ngày bị phá vỡ, người dùng mất thời gian và dễ bỏ sót
task quan trọng khi xây lại lịch cho phần thời gian còn lại.

Actor:
Sinh viên và knowledge workers có nhiều task/deadline.

Thời điểm / bối cảnh:
Sau cuộc họp bất ngờ, task overrun, việc khẩn, thay đổi energy/health hoặc task mới.

Current workflow:
1. Mở lịch/task list hiện tại.
2. Xác định task đã trễ và thời gian còn lại.
3. Đọc lại deadline, importance, effort và dependency từng task.
4. Tự đổi thứ tự hoặc kéo task sang ngày khác.
5. Kiểm tra lịch mới rồi tiếp tục làm.

Bottleneck:
Bước 2-4: re-evaluate và re-plan thủ công, thường phải so sánh nhiều task
trong khi người dùng đang mất tập trung vì disruption.

Impact:
Tăng thời gian planning, tạo task rollover và có nguy cơ làm trễ task quan trọng.

Success metric:
Giảm replanning time >=40%; suggestion acceptance khoảng 70%; giảm rollover 20-30%;
không giảm important-task completion và không tăng perceived workload.

Non-AI alternative:
Một form disruption + weighted scoring cố định + template lịch lại.

AI hypothesis:
AI có thể giải thích trade-off và đề xuất lịch dễ hiểu từ context còn lại,
nhưng chỉ sau rule/scoring và luôn chờ user approve.

Quick gut: [ ] No AI  [ ] Rule  [x] Workflow  [ ] Agent  [ ] Chưa biết
```

**Draft workflow Card #1:**

```text
CURRENT STATE — 10-20 phút giả định, cần đo baseline
[Plan/Execute] → [Disruption] → [Đọc lại task + deadline] →
[Tự đổi thứ tự thủ công — BOTTLENECK] → [Tiếp tục hoặc rollover]

FUTURE STATE — mục tiêu dưới 60% baseline
[Log disruption] → [Rule/scoring tính lại] →
[Bounded AI giải thích 2-3 phương án] → [User review/approve] → [Continue]

Human boundary: user luôn approve; hệ thống không tự hủy/sửa commitment quan trọng.
Fallback: scoring/template deterministic nếu AI lỗi, thiếu dữ liệu hoặc confidence thấp.
```

### Problem Card #2 — Multi-factor task prioritization

```text
Problem 1 câu:
Khi có nhiều task cạnh tranh, người dùng khó chọn thứ tự làm mà không bỏ sót
deadline, importance hoặc dependency.

Actor:
Sinh viên, developer và knowledge worker.

Thời điểm / bối cảnh:
Đầu ngày và ngay sau khi có task mới hoặc lịch bị xáo trộn.

Current workflow:
1. Xem danh sách task.
2. Nhớ hoặc kiểm tra deadline.
3. Ước lượng effort và importance bằng cảm tính.
4. Đổi thứ tự task.
5. Bắt đầu task đầu tiên.

Bottleneck:
Bước 2-4 vì nhiều tiêu chí không được so sánh nhất quán.

Impact:
Task quan trọng có thể bị trì hoãn; người dùng mất thời gian quyết định và đổi priority.

Success metric:
Giảm thời gian chọn priority 40%; 90% task quan trọng được đưa vào lịch;
không tăng số task quan trọng bị trễ.

Non-AI alternative:
Eisenhower Matrix hoặc weighted score có trọng số do user chỉnh.

AI hypothesis:
AI giải thích vì sao score đề xuất thứ tự, nêu trade-off và hỏi user khi dữ liệu xung đột.

Quick gut: [ ] No AI  [x] Rule  [x] Workflow  [ ] Agent  [ ] Chưa biết
```

**Draft workflow Card #2:**

```text
CURRENT STATE — 8-15 phút giả định
[Task list] → [Nhớ deadline] → [Ước lượng cảm tính] → [Đổi priority — BOTTLENECK]

FUTURE STATE — 3-5 phút mục tiêu
[Structured task fields] → [Weighted score + dependency rules] →
[AI explanation] → [User review]

Fallback: hiển thị bảng score và để user kéo-thả thủ công; không tự đổi commitment.
```

### Problem Card #3 — Effort overrun và schedule drift

```text
Problem 1 câu:
Khi actual effort dài hơn estimate, các task sau bị trượt và người dùng phải
re-plan nhiều lần.

Actor:
Sinh viên và knowledge worker làm task cần tập trung.

Thời điểm / bối cảnh:
Trong phiên làm việc có task khó, interruption hoặc estimate thiếu dữ liệu.

Current workflow:
1. Nhập estimated effort.
2. Xếp task vào lịch.
3. Thực hiện task.
4. Task overrun.
5. Kéo các task phía sau và tiếp tục bị lệch.

Bottleneck:
Bước 4-5: nhận ra drift muộn và sửa cả phần lịch còn lại.

Impact:
Task rollover, perceived workload và nguy cơ trễ deadline tăng.

Success metric:
Giảm task rollover 20-30%; giảm median schedule drift 25%; không làm giảm completion
của task importance cao.

Non-AI alternative:
Timebox, buffer cố định và cập nhật actual effort sau mỗi phiên.

AI hypothesis:
Agent bounded đề xuất điều chỉnh effort/buffer dựa trên lịch sử, nhưng không tự ghi đè
estimate gốc hoặc thay đổi commitment nếu chưa được duyệt.

Quick gut: [ ] No AI  [x] Rule  [x] Workflow  [ ] Agent  [ ] Chưa biết
```

**Draft workflow Card #3:**

```text
CURRENT STATE — theo dõi sau mỗi phiên
[Estimate] → [Schedule] → [Execute] → [Overrun] → [Kéo lịch thủ công — BOTTLENECK]

FUTURE STATE
[Start/stop timer] → [Rule phát hiện overrun] → [Recalculate remaining time]
→ [User review revised schedule]

Fallback: thêm buffer cố định và yêu cầu user chọn task bị đẩy; giữ lại audit log.
```

### 2.3. Card muốn pitch nhất

**Card tôi muốn pitch nhất:** Card #1 — Adaptive re-planning sau disruption.

**Vì sao:** Đây là pain trung tâm, nối trực tiếp disruption với prioritization, scheduling và rollover. MVP có thể đo trước/sau bằng thời gian re-plan, acceptance, rollover và important-task completion. Boundary rõ vì AI chỉ recommend, còn user duyệt.

**Câu hỏi muốn nhóm challenge:**

1. Rule/scoring có giải quyết đủ 70–80% case mà không cần Agent không?
2. Làm sao chứng minh acceptance tăng nhưng perceived workload không tăng?

**AI phản biện Card:**

- Điểm yếu: chưa có baseline thật; “70% acceptance” có thể không đồng nghĩa lịch tốt; việc đánh giá energy/health có tính chủ quan.
- Tôi sửa: tách baseline giả định khỏi số đo, thêm log recommendation/edit/reject, giữ user approval và định nghĩa guardrail cho important commitments.

### Self-check nộp phần 01

- [x] Có 8 problems + top 3 Problem Cards đủ field.
- [x] Mỗi Card có workflow trước/sau, bottleneck, metric và fallback.
- [x] Đã chọn 1 card pitch + câu hỏi challenge.
