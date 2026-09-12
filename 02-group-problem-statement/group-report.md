# 02 — Group Problem Statement: Adaptive Planning System

> Bản này là architecture proposal dựa trên context đã cung cấp. Tên thành viên khác và bằng chứng interview/survey chưa được cung cấp nên được đánh dấu pending, không bịa thành viên hoặc quote.

## Thành viên nhóm

| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|---|---|---|---|
| 1 | Nguyễn Hồng Khoa | 2A202602534 | Problem framing, architecture, workflow, writer |
| 2 | Chưa cung cấp | Chưa cung cấp | Cần nhóm bổ sung |
| 3 | Chưa cung cấp | Chưa cung cấp | Cần nhóm bổ sung |
| 4 | Chưa cung cấp | Chưa cung cấp | Cần nhóm bổ sung |

**Candidate problem nhóm chọn:** Khi kế hoạch trong ngày bị phá vỡ bởi disruption, task overrun, workload mới hoặc thay đổi energy/health, sinh viên và knowledge worker mất nhiều thời gian để đánh giá lại và xây lịch còn lại; họ cần recommendation có giải thích nhưng vẫn giữ quyền duyệt.

---

## Phase 3 — Group Convergence

### 3.1. Candidates để nhóm review

| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---|---|---|---|---|---|
| 1 | Khoa | Re-plan sau disruption | Sinh viên, knowledge worker | Đánh giá lại task còn lại | Khớp core problem, đo được |
| 2 | Khoa | Ưu tiên khi nhiều deadline | Người có nhiều task | So sánh deadline/importance/effort | Có thể bắt đầu bằng rule |
| 3 | Khoa | Effort overrun làm schedule drift | Người làm task tập trung | Phát hiện và xử lý overrun | Là input quan trọng cho re-plan |
| 4 | Cần bổ sung | Chưa cung cấp | Chưa cung cấp | Chưa cung cấp | Chờ group convergence |
| 5 | Cần bổ sung | Chưa cung cấp | Chưa cung cấp | Chưa cung cấp | Chờ group convergence |
| 6 | Cần bổ sung | Chưa cung cấp | Chưa cung cấp | Chưa cung cấp | Chờ group convergence |
| 7 | Cần bổ sung | Chưa cung cấp | Chưa cung cấp | Chưa cung cấp | Chờ group convergence |
| 8 | Cần bổ sung | Chưa cung cấp | Chưa cung cấp | Chưa cung cấp | Chờ group convergence |
| 9 | Cần bổ sung | Chưa cung cấp | Chưa cung cấp | Chưa cung cấp | Chờ group convergence |

### 3.2. Cluster

| Cluster | Candidates included | Pattern chung | Ghi chú |
|---|---|---|---|
| A — Re-planning | #1 | Xây lại lịch còn lại sau disruption | Candidate chính |
| B — Prioritization | #2 | Đánh giá thứ tự task theo nhiều tiêu chí | Rule/scoring layer |
| C — Schedule accuracy | #3 | Estimate, actual effort và rollover | Feedback data cho engine |
| D — Bổ sung từ nhóm | #4–#9 | Chưa có dữ liệu | Phải bổ sung trước khi chốt bản group chính thức |

### 3.3. Shortlist

| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| Adaptive re-planning sau disruption | Actor rõ; workflow từ Plan → Disruption → Re-plan; metric và MVP rõ. | Chưa có baseline thật; cần test nhiều loại disruption. |
| Multi-factor prioritization | Có thể dùng Eisenhower, impact–effort và weighted scoring; dễ làm deterministic. | Score có thể không phản ánh preference/energy của từng người. |
| Effort overrun detection | Dữ liệu planned/actual có thể log; hỗ trợ giảm rollover. | Cần lịch sử đủ dài và phân biệt overrun với interruption. |

### 3.4. Score để đồng thuận

Thang điểm 1–5; hiện là score phân tích sơ bộ, cần nhóm xác nhận.

| Candidate | Actor rõ | Workflow rõ | Pain evidence | Impact đo được | Làm trong lab | So sánh R/W/A | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Adaptive re-planning | 5 | 5 | 3 | 5 | 5 | 5 | 4 | 32 |
| Prioritization | 5 | 4 | 3 | 4 | 5 | 5 | 4 | 30 |
| Effort overrun | 5 | 4 | 3 | 4 | 4 | 4 | 4 | 28 |

**Candidate nhóm chọn:** Adaptive re-planning sau disruption, có prioritization và overrun detection là supporting capabilities.

**Vì sao chọn:** Bài toán có một bottleneck trung tâm, nhưng đủ chiều sâu để kiểm tra rule, workflow và bounded agent. MVP có thể bắt đầu với 6–10 task, một disruption và một revised schedule. User approval tạo boundary rõ, đồng thời các metric đều có thể log.

**Vì sao không chọn candidate còn lại:** Prioritization là một module của re-planning, không bao phủ trigger và lịch còn lại. Effort overrun là nguyên nhân/feedback signal, nhưng riêng nó chưa giải quyết việc user phải chọn lại toàn bộ task sau disruption.

**Disagreement:** Chưa có biên bản thảo luận nhóm thực tế. Điểm cần thống nhất là trọng số scoring, định nghĩa “important commitment” và có cho phép AI đề xuất bỏ task hay chỉ đề xuất dời task.

---

## Phase 4 — Quick Validation + Research

### 4.1. Quick validation

| Nguồn | Số người / mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Interview | Pending | Chưa thực hiện; không ghi quote giả. | Chưa biết nhóm người dùng nào đau nhất. | Phỏng vấn 2–3 sinh viên/knowledge worker, hỏi một disruption gần đây và bấm giờ re-plan. |
| Survey / poll | Pending | Chưa thực hiện. | Chưa biết acceptance target 70% có thực tế. | Survey 5–10 người, đo frequency, replanning time, rollover và perceived workload. |
| Log cá nhân | 1 người / cần mở rộng | Context hiện tại mô tả rõ workflow và metric cần đo. | Một người không đại diện cho toàn bộ actor. | Dùng log cá nhân làm pilot baseline, không dùng làm bằng chứng tổng quát. |

**Insight sau validation:** Hiện mới có problem hypothesis, chưa thể gọi là pain đã validate. Ưu tiên validation là đo thời gian re-plan và task rollover sau disruption; nếu pain thấp, thu hẹp scope sang nhóm có workload/deadline cao.

### 4.2. Research giải pháp / pattern

| Nguồn / tool / pattern | Link | Họ giải quyết bước nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học |
|---|---|---|---|---|---|
| Eisenhower Matrix | https://www.eisenhower.me/eisenhower-matrix/ | Phân loại urgent/important | Dễ hiểu, deterministic | Hai chiều không đủ cho dependency và effort | Dùng như explainable view, không làm engine duy nhất. |
| OR-Tools CP-SAT / scheduling pattern | https://developers.google.com/optimization/cp | Constraint scheduling và time allocation | Mạnh với constraint/dependency | Cần model hóa dữ liệu và không giải thích preference tự nhiên | Dùng rule/constraint layer trước AI. |
| OpenAI Structured Outputs | https://platform.openai.com/docs/guides/structured-outputs | Trả recommendation theo schema | Giảm output sai format | Schema đúng không đảm bảo recommendation đúng | LLM chỉ nhận context, trả plan proposal có confidence/reason. |

**Research takeaway:** Nên build hybrid: structured task data + deterministic scoring/constraint checks + bounded AI để giải thích và tạo vài phương án. Không build agent có quyền tự hủy, dời hoặc thay đổi important commitments.

---

## Phase 5 — Workflow + Problem Statement

### 5.1. Current workflow

```text
[1 Plan: 10' - user] → [2 Execute: theo lịch] → [3 Disruption: 1-5' - user] →
[4 Re-evaluate: 5-10' - user, BOTTLENECK] → [5 Re-prioritize: 5-10'] →
[6 Re-plan: 5-10'] → [7 Continue / rollover]
```

| Bước | Actor | Input | Output | Thời gian / tần suất | Handoff / bottleneck |
|---|---|---|---|---|---|
| 1. Plan | User | 6–10 task, deadline, effort | Daily schedule | Đầu ngày | User nhập dữ liệu |
| 2. Execute | User | Current task | Progress/actual effort | Mỗi phiên | Có thể phát sinh overrun |
| 3. Disruption | User/system | Event mới, interruption, energy | Disruption event | Khi phát sinh | Handoff event → planning state |
| 4. Re-evaluate | User | Task chưa xong, thời gian còn lại | Candidate remaining tasks | 5–10 phút | **Bottleneck** |
| 5. Re-prioritize | User | Deadline, importance, effort, dependency | New priority order | 5–10 phút | Dễ bị cảm tính |
| 6. Re-plan | User | Priority + time windows | Revised schedule | 5–10 phút | Dễ rollover |
| 7. Continue | User | Approved schedule | Completed/rolled tasks | Phần còn lại | Feedback cho ngày sau |

**Bottleneck chính:** Re-evaluate, re-prioritize và re-plan xảy ra khi user đã mất focus. Người dùng phải vừa nhớ context vừa cân bằng deadline, importance, effort, dependency, workload và energy.

### 5.2. Future workflow

```text
[1 Create tasks - user] → [2 Initial schedule - Rule/scoring] →
[3 Execute + log actual] → [4 Capture disruption - Rule] →
[5 Recalculate remaining priorities - Rule] →
[6 Generate 2-3 revised schedules - bounded AI] →
[7 User edits/accepts/rejects - HITL boundary] → [8 Continue + record metrics]

Fallback: AI timeout/invalid output/low confidence → deterministic score + manual editor.
Important commitments are never auto-cancelled or auto-modified.
```

**Before/after impact:**

| Metric | Trước | Sau kỳ vọng | Cách đo |
|---|---:|---:|---|
| Replanning time | Baseline cần đo | Giảm ít nhất 40% | Timer từ disruption đến approved schedule |
| Suggestion acceptance | Chưa có | Khoảng 70% | Accepted / total suggestions; tách edit/reject |
| Task rollover | Baseline cần đo | Giảm 20–30% | Rollover count theo ngày/tuần |
| Important-task completion | Baseline cần đo | Không giảm | Completion đúng hạn của task importance cao |
| Perceived workload | Baseline 1–5 | Không tăng | User rating trước/sau re-plan |

### MVP architecture proposal

```text
Frontend (task list, timeline, disruption dialog, proposal review)
        ↓ REST/JSON
Backend API + deterministic planning service
        ├─ Task/revision/approval/metric storage
        ├─ Rule & weighted scoring layer
        ├─ Schedule constraint validator
        └─ Bounded AI adapter (recommendation only)
                ↓ structured proposal
        Human approval → schedule revision → audit/metrics
```

**Rule/scoring layer:** validate fields, calculate deadline pressure/importance/effort/dependency/workload/energy score, protect locked commitments and check time feasibility.

**Deterministic workflow:** `create_tasks → schedule → execute → disruption → recalculate → propose → approve/edit/reject → continue`. Every transition is auditable and idempotent.

**Bounded AI agent:** receives only remaining task context and constraints; returns 2–3 candidate schedules with reasons, trade-offs, confidence and unknowns. It cannot call cancellation, deletion or commitment-edit tools.

**Human approval:** user selects, edits or rejects. Important commitments require explicit confirmation; rejection keeps the previous schedule.

### Database schema proposal

| Table | Key fields | Purpose |
|---|---|---|
| `users` | `user_id`, `timezone`, `default_energy_profile` | User preferences and timezone. |
| `tasks` | `task_id`, `user_id`, `title`, `deadline`, `importance`, `estimated_effort_min`, `dependency_ids`, `priority`, `status`, `is_commitment_locked` | Canonical task records. |
| `daily_plans` | `plan_id`, `user_id`, `date`, `available_minutes`, `energy_level`, `version`, `status` | One daily planning state/version. |
| `plan_items` | `plan_item_id`, `plan_id`, `task_id`, `start_at`, `end_at`, `sequence`, `state` | Scheduled task slots. |
| `disruptions` | `disruption_id`, `plan_id`, `type`, `duration_min`, `occurred_at`, `notes` | Event that triggers re-planning. |
| `recommendations` | `recommendation_id`, `plan_id`, `input_snapshot_json`, `candidate_plan_json`, `reasoning_summary`, `confidence`, `model_version`, `created_at` | AI/rule proposal and audit context. |
| `approvals` | `approval_id`, `recommendation_id`, `decision`, `edited_plan_json`, `decided_at` | Accept/edit/reject and user choice. |
| `task_events` | `event_id`, `task_id`, `event_type`, `actual_minutes`, `created_at` | Start/stop/overrun/completion history. |
| `metrics` | `metric_id`, `plan_id`, `replan_seconds`, `accepted`, `rollover_count`, `important_completed`, `workload_rating` | MVP evaluation metrics. |

Use foreign keys, UTC timestamps plus user timezone, immutable recommendation snapshots and optimistic plan versioning to prevent lost updates.

### Frontend pages / components

1. **Today dashboard:** timeline, remaining minutes, energy check-in, workload and task status.
2. **Task editor:** title, deadline, importance, effort, dependency, priority, lock commitment.
3. **Disruption dialog:** type, duration, new task, energy change and “re-plan” action.
4. **Revised schedule review:** before/after diff, reasons, trade-offs, warning for rollover, accept/edit/reject buttons.
5. **Task detail/history:** actual effort, dependency graph and audit events.
6. **Metrics page:** replanning time, acceptance/edit/reject, rollover, important completion and workload trend.

### Implementation milestones

| Milestone | Scope | Exit criteria |
|---|---|---|
| M0 — Baseline and safety contract | Interview/survey, 5–7 day manual log, define important commitment, metric formulas and rollback thresholds. | Baseline for replan time, rollover, completion and workload; approved boundary document. |
| M1 — Task and plan foundation | Implement task fields, dependency validation, daily plan versions, timeline and event logging. | User can create 6–10 tasks, create an initial schedule and record actual effort. |
| M2 — Deterministic planning engine | Add deadline pressure, importance, effort, dependency, workload and energy scoring; add time feasibility and locked commitment checks. | Same input produces reproducible priority/order; invalid or conflicting schedules are rejected. |
| M3 — Disruption and revision workflow | Add disruption event, remaining-task recalculation, before/after diff, accept/edit/reject and audit records. | User can trigger a disruption and approve or reject a revised deterministic schedule. |
| M4 — Bounded AI recommendation | Add structured AI adapter after rule validation; request 2–3 alternatives with reasons/confidence; enforce schema and timeout fallback. | AI cannot execute commitment changes; invalid/low-confidence output falls back to rule/manual flow. |
| M5 — Pilot and evaluation | Run baseline vs prototype with 5–10 users; monitor acceptance, edits, rejects, rollover, important completion and workload. | Go/no-go decision based on ≥40% replan-time target, 20–30% rollover target and safety guardrails. |

### Where rules end and AI begins

| Area | Rule / deterministic | AI agent |
|---|---|---|
| Input validation | Required fields, deadline format, dependency cycle, locked commitment | Ask clarification in natural language only |
| Priority | Weighted score, deadline pressure, feasibility, hard constraints | Explain why a candidate order is reasonable |
| Scheduling | Available time, no overlap, dependency order, locked events | Generate 2–3 human-readable alternatives within constraints |
| Safety | Never auto-cancel/modify important commitment; reject invalid output | No permission to execute destructive/commitment actions |
| Fallback | Existing schedule, score table, manual editor | Not used when timeout, low confidence or invalid schema |

### 5.3. Problem Statement v0

| Field | Nội dung |
|---|---|
| Actor | Students and knowledge workers managing multiple tasks and deadlines. |
| Workflow | User plans, executes, encounters disruption, evaluates remaining tasks, reprioritizes, replans and continues. |
| Bottleneck | Re-evaluating and rebuilding the remaining day after disruption. |
| Impact | Replanning consumes time, increases rollover and can reduce completion of important tasks while perceived workload rises. |
| Success Metric | Replanning time -40% or better; acceptance around 70%; rollover -20–30%; important completion not reduced; workload not increased. |
| Boundary | Recommendation only; user approves. No autonomous cancellation or modification of important commitments. |

**AI phản biện v0:** “70% acceptance” cần tách accepted/edited/rejected; “important” cần định nghĩa; baseline chưa có. **Tôi sửa:** thêm lock commitment, approval audit, baseline run và exact metric formulas.

---

## Phase 6 — Rule / Workflow / Agent + Decision

### 6.0. Ma trận độ phù hợp

- Độ mơ hồ: **Cao vừa phải** — mục tiêu “lịch tốt” phụ thuộc energy, preference và trade-off; nhưng deadline, dependency và locked commitment có thể kiểm tra rõ.
- Độ phức tạp: **Cao** — nhiều bước, state changes, constraints và feedback từ actual effort.

**Bài toán nằm ở ô:** Workflow deterministic có bounded AI assistance, không phải autonomous Agent.

### 6.1. So sánh Rule / Workflow / Agent

| Mức | Phương án | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| Rule | Weighted score + deadline/dependency constraints | 70–80% case có field đầy đủ và preference ổn định | Cứng, khó giải thích trade-off tự nhiên | Chọn cho validation, scoring, safety |
| Workflow | State machine với disruption → proposal → approval | Hầu hết flow có bước cố định | Cần xử lý nhiều loại event | **Chọn làm backbone** |
| Agent | Tự lập kế hoạch và gọi tool thay user | Chỉ khi scope rộng và quyền hạn được khóa | Tự ý sửa/hủy commitment, khó audit | Không chọn autonomous; chỉ bounded recommendation |

**5 câu hỏi chốt:**

1. Rule có thể giải 70–80% case có cấu trúc; phần còn lại cần explanation/clarification.
2. Các bước chính đi theo state machine nhưng disruption type tạo nhánh.
3. Chưa cần Agent tự lập kế hoạch + gọi tool vì MVP chỉ cần proposal.
4. User phát hiện sai ngay trên diff; nếu AI sai, user reject/edit trong lần review.
5. Có thể hạ về Workflow → Rule + manual editor bất cứ lúc nào.

**Mức chọn:** Workflow + Rule, có bounded AI feature.

**Vì sao:** Core process có state rõ và cần audit. Rule bảo vệ deadline/dependency/commitment; AI chỉ tạo explanation và alternatives khi preference hoặc trade-off khó biểu diễn. Human approval là bước bắt buộc.

**Vì sao không chọn Agent thuần:** Agent có thể hành động ngoài ý muốn trong một lịch có deadline thật. MVP chưa có đủ dữ liệu để cho agent tự học hoặc tự sửa commitment.

### 6.2. Problem Statement v1

| Field | Nội dung |
|---|---|
| Actor | Students and knowledge workers with 6–10 daily tasks and at least one deadline/priority constraint. |
| Workflow | Task entry → initial deterministic schedule → execute/log → disruption → deterministic recalculation → bounded AI proposal → user review → approved revision → metrics. |
| Bottleneck | User manually compares remaining tasks after disruption while context/time/energy are changing. |
| Impact | Long replanning time, 20–30% target rollover reduction opportunity, and risk to important-task completion. Baseline must be collected before claiming improvement. |
| Success Metric | Replanning time reduction ≥40%; acceptance around 70%; rollover reduction 20–30%; no decrease in important-task completion; no increase in workload rating. |
| Boundary | Does: rank, explain, suggest schedule alternatives, record metrics. Does not: autonomously cancel, delete, reschedule locked commitments, send messages, or claim a plan is optimal. |
| AI intervention point | After rule validation and deterministic scoring, before user approval; never directly after raw user text without validation. |
| Mức chọn | Workflow + Rule with bounded AI recommendation because the state transitions and safety constraints are deterministic, while explanation/alternatives benefit from language reasoning. |
| Rủi ro & người thật kiểm tra | Wrong ranking or hidden commitment change; user reviews a before/after diff and can edit/reject, while product owner reviews weekly safety/metric logs. |

### 6.3. Final decision

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor + workflow rõ chưa? | Yes | Actor, disruption flow and bottleneck are explicit. |
| Baseline + metric đo được chưa? | Not Yet | Metric is defined but needs 5–7 day baseline log. |
| Data/input đủ dùng chưa? | Not Yet | MVP can start with 6–10 tasks, but dependency/energy data need validation. |
| AI sai, hậu quả chấp nhận được không? | Yes with HITL | AI cannot execute commitment changes; user reviews every proposal. |
| Có người review/owner không? | Yes | User is approval owner; product owner reviews pilot metrics. |
| Có cách non-AI đơn giản hơn không? | Yes, for core | Rule/workflow handles safety and common cases; AI is only bounded explanation/alternative. |

**Decision: Go cho prototype/pilot hẹp, chưa Go cho autonomous production.**

**Lý do:** MVP có scope rõ, data schema nhỏ và fallback deterministic. Tuy nhiên baseline và validation chưa đủ để cam kết business impact; pilot phải đo trước/sau và giữ HITL. Chỉ mở rộng sau khi không giảm important-task completion và không tăng perceived workload.

**Pilot nhỏ nhất:** 6–10 task/ngày, 1 người dùng hoặc 5–10 pilot users, 1 disruption mỗi test scenario. Chạy manual baseline trước, sau đó bật proposal review. Đo 3 số chính: `replan_seconds`, `rollover_count`, `important_completion`; bổ sung acceptance và workload rating.

**Not Yet — cần validate trước production:** frequency/type of disruptions, baseline replanning time, meaning of “important commitment”, weight personalization và whether 70% acceptance correlates with better outcomes.

**Exit / rollback:** dừng AI nếu invalid-schema rate, accidental commitment change, workload rating hoặc important-task miss vượt threshold được team đặt ra; quay về previous schedule + deterministic score/manual editor.

### Self-check nộp phần 02

- [x] Có convergence/cluster/shortlist/score; phần tên thành viên còn thiếu được đánh dấu minh bạch.
- [x] Có validation plan và research links; chưa bịa quote chưa được cung cấp.
- [x] Có workflow trước/sau, thời gian, handoff, bottleneck, boundary và fallback.
- [x] Có PS v0 → v1, metric trước/sau và cách đo.
- [x] Có so sánh Rule/Workflow/Agent và quyết định Go có điều kiện.
