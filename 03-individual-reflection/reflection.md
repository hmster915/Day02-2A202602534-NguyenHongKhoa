# 03 — Individual Reflection

> Bản reflection này là draft theo context và phần phân tích đã làm. Các chi tiết về nhóm/interview chưa được cung cấp được đánh dấu rõ để tránh biến giả định thành sự thật.

## Thông tin cá nhân

- Họ và tên: Nguyễn Hồng Khoa
- Mã học viên: 2A202602534
- Nhóm: Chưa cung cấp tên nhóm
- Candidate problem nhóm chọn: Adaptive re-planning sau disruption cho sinh viên và knowledge workers.

---

## 1. Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng tới nhóm |
|---|---|---|
| Scan cá nhân | Liệt kê pain points về disruption, deadline, effort overrun, dependency, energy và rollover; ghi cách đo cho từng pain. | Thu hẹp từ nhiều ý tưởng productivity về một bottleneck có workflow rõ: re-plan phần ngày còn lại. |
| Pitch Problem Card | Chuẩn bị Card #1 với flow Plan → Execute → Disruption → Re-plan → Approval → Continue. | Đề xuất một problem có metric và operational boundary rõ. |
| Challenge bài của bạn khác | Đặt câu hỏi liệu weighted score/rule có giải được phần lớn case trước khi cần Agent hay không. | Giúp tránh solution-first và tránh trao quyền tự động quá sớm cho AI. |
| Gom trùng / cluster | Gom re-planning, prioritization và effort overrun thành một hệ thống; xem prioritization/overrun là supporting capability. | Làm rõ core problem không phải “AI làm lịch”, mà là recovery sau disruption. |
| Chọn candidate problem | So sánh actor, bottleneck, metric, feasibility và risk của 3 candidate. | Chọn adaptive re-planning làm candidate chính. |
| Validation / research | Xác định baseline cần đo và tìm pattern Eisenhower, OR-Tools scheduling, Structured Outputs. | Phân biệt research pattern với evidence pain; đánh dấu interview/survey là pending. |
| Workflow nhóm | Viết current/future flow, handoff, thời gian giả định, HITL và fallback. | Chỉ ra bước re-evaluate/re-prioritize/re-plan là bottleneck. |
| Problem Statement | Viết PS v0/v1 với metric, boundary, intervention point và người kiểm tra rủi ro. | Chuyển ý tưởng rộng thành MVP có thể pilot. |
| Rule / Workflow / Agent | Đề xuất rule/scoring + state machine + bounded AI, không autonomous agent. | Bảo vệ important commitments và giữ đường rollback. |
| Decision | Chọn Go cho prototype/pilot hẹp, chưa Go cho autonomous production. | Gắn quyết định với baseline, HITL và threshold đo được. |

**Dấu tay rõ nhất của tôi trong artifact cuối:** Phần rõ nhất là ranh giới giữa rule, workflow và AI: rule kiểm tra constraint, workflow điều phối state, AI chỉ tạo recommendation/explanation, user luôn approve. Tôi cũng thêm các metric không chỉ đo acceptance mà còn kiểm tra important-task completion và perceived workload để tránh tối ưu sai.

---

## 2. Bảng dùng AI

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai / hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Brainstorm pain points từ context sinh viên/knowledge worker. | Gợi ý các lăng kính deadline, effort, dependency, energy và rollover. | Dễ nhảy ngay sang “AI productivity assistant” thay vì pain có bằng chứng. | Giữ problem trước solution và thêm cách đo/baseline cho từng dòng. |
| Problem Card | Stress-test actor, workflow, metric và non-AI alternative. | Giúp so sánh re-planning với prioritization và overrun. | Có thể đề xuất Agent vì nghe hấp dẫn dù rule đủ cho case cơ bản. | Chọn workflow/rule làm backbone, AI chỉ bounded recommendation. |
| Workflow | Chuyển core workflow thành current/future state. | Làm rõ handoff, bottleneck, fallback và HITL. | Không thể tự biết thời gian thực tế của tôi. | Ghi thời gian là giả định cần bấm giờ, không gọi là evidence. |
| Research | Gợi ý pattern/tools để tìm tài liệu chính thức. | Định hướng Eisenhower, scheduling constraints và structured output. | Link/pattern không tự chứng minh người dùng có pain hoặc hiệu quả đạt metric. | Chỉ coi nguồn là design input; yêu cầu validation riêng. |
| Problem Statement | Kiểm tra đủ 6 field và thêm intervention/boundary/risk owner. | Giúp phát hiện thiếu definition cho “important”. | Acceptance 70% có thể bị coi là success duy nhất. | Thêm completion và workload guardrails, lock commitment và approval audit. |
| Rule / Workflow / Agent | So sánh mức tự động hóa. | Làm nổi bật quyền hạn và rollback. | AI có xu hướng mô tả agent quá rộng. | Giới hạn tool/action và đặt fallback deterministic/manual. |
| Decision | Phản biện Go/Not Yet dựa trên MVP. | Giúp tách “Go prototype” khỏi “Go production”. | Không thể thay validation thực tế. | Chọn Go có điều kiện; baseline và interview vẫn là gate trước production. |

---

## 3. Reflection câu hỏi mở

Điều tôi học được là cùng một chủ đề “quản lý task” có thể bị mô tả quá rộng nếu chỉ bắt đầu từ solution. Khi tách workflow, bottleneck trở nên cụ thể hơn: vấn đề không phải người dùng không có app todo, mà là họ khó phục hồi kế hoạch sau khi ngày làm việc bị phá vỡ. Tôi cũng nhận ra acceptance của AI không đủ để chứng minh sản phẩm tốt, vì người dùng có thể bấm accept để tiết kiệm thời gian nhưng vẫn bỏ lỡ task quan trọng. Vì vậy nhóm cần đo cả important-task completion, rollover và perceived workload. Điểm dễ bị solution-first nhất là muốn làm một Agent tự lập kế hoạch và tự sửa lịch, nhưng phần rule và state machine đã giải quyết được safety và nhiều case phổ biến. AI chỉ nên bắt đầu sau khi dữ liệu task đã có cấu trúc và constraint được kiểm tra. Nếu làm lại, tôi sẽ challenge mạnh hơn về baseline: cần bấm giờ re-plan trước khi đặt mục tiêu giảm 40%. Tôi cũng sẽ yêu cầu định nghĩa “important commitment” và test các trường hợp disruption khác nhau trước khi kết luận. Với MVP, tôi thấy cách an toàn nhất là cho AI tạo vài phương án, hiển thị diff và để user approve hoặc reject. Cách này làm prototype nhỏ hơn nhưng giúp biết recommendation có thật sự giảm workload hay chỉ tạo thêm một lớp xem xét.

---

## 4. Tự kiểm cuối bài

- [x] Cá nhân có 8 problems + top 3 Problem Cards.
- [x] Đã pitch rõ và ghi câu hỏi challenge nhóm.
- [x] Đã mô tả convergence theo dữ liệu hiện có; phần chưa có được đánh dấu pending.
- [x] Nhóm có workflow trước/sau, metric và boundary trong group report.
- [x] Group report có PS v0/v1.
- [x] Có so sánh No AI / Rule / Workflow / Agent.
- [x] Có quyết định Go có điều kiện và rollback.
- [x] Reflection nêu vai trò, AI giúp/sai, bài học và điều sẽ đổi.
- [x] Có thể giải thích mạch problem → workflow → metric → boundary → AI fit.
