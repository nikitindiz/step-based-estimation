# Step-Based Estimation (SBE) Methodology

## Methodology Description

**Step-Based Estimation** is a development planning approach where each task is decomposed into detailed, concrete execution steps, followed by dependency analysis and optional retrospective comparison of plan versus reality.

In addition to Acceptance Criteria, which typically represent a declarative view of the task, Implementation Steps provide an imperative description of how exactly the task will be implemented.

### SBE Process:

**Work Organization:**

- **Refinement Session (existing)**: Standard task estimation through agile poker
- **Step Estimation Session (new)**: Separate meeting for detailed decomposition

**Task Selection for Detailing**: Tasks are brought to Step Estimation based on team voting results

**Task Work Stages:**

1. **Decomposition**: Break down the task into concrete steps ("Add field X to form Y", "Update function Z in module W", "Create repository for data source Y").
2. **Hidden Subtask Discovery**: Identify steps that can be extracted into separate tasks.
3. **Estimation**: Evaluate the task by total number of steps (using Fibonacci).
4. **Retrospective** _(optional)_: Compare planned steps with actually completed ones, identify divergence patterns, take into account for future estimations.

---

## Comparison of Estimation Approaches

| Aspect                | Refinement (optimistic)                                                                                          | Step Estimation (pessimistic)                                                                                                                                                                                                                                                                                                                               |
| --------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Character**         | High-level, fast, based on general understanding                                                                 | Detailed, based on concrete implementation steps                                                                                                                                                                                                                                                                                                            |
| **When It Occurs**    | • At initial planning stage<br>• During first encounter with task<br>• Based on Acceptance Criteria              | • After Refinement, before sprint start<br>• For complex/risky tasks<br>• Based on Implementation Steps                                                                                                                                                                                                                                                     |
| **Advantages**        | ✓ Fast                                                                                                           | ✓ Considers details<br>✓ Reveals hidden steps<br>✓ More realistic                                                                                                                                                                                                                                                                                           |
| **Disadvantages**     | ⚠ Prone to underestimating complexity<br>⚠ Doesn't account for implementation details<br>⚠ Misses "hidden" steps | ⚠ Requires more time<br>⚠ Requires technical expertise                                                                                                                                                                                                                                                                                                      |
| **Typical Questions** | • "Is this roughly like that task?"<br>• "Sounds like 5 points"<br>• "Acceptance Criteria look simple"           | • "What classes, modules, and functions need to be changed?"<br>• "What repositories and data sources are affected?"<br>• "What states need to be considered?"<br>• "If we treat the software entity as a black box, what interface describes the arguments and return value?"<br>• "If there are dependent tasks, how do they integrate after completion?" |

---

## Synergy of Two Approaches

### Classic Problem (Refinement Only)

```
Team at Refinement: "Add table filters — 3 points!"

Reality during sprint:
- Day 1: "Oh, need to redesign database structure"
- Day 2: "Oh, need to add indexes for performance"
- Day 3: "Oh, need to handle edge cases with empty data"
- Day 4: "Oh, need to adapt UI for mobile devices"
- Day 5: "Oh, need to write 15 tests instead of 5"

Result: 3 SP turned into 8 SP, task didn't fit in sprint
```

### With SBE Application (Refinement + Step Estimation)

```
Refinement (optimistic): 3 SP
↓
Team voting: bring to Step Estimation
↓
Step Estimation (pessimistic): detailing reveals:
- 12 steps instead of assumed 5
- Database migration needed
- Will require 15 tests
- 6 classes affected
↓
Correction: 3 SP → 5 SP
↓
Result: more realistic estimate, task fits in sprint
```

### Estimation Psychology

**Refinement (optimism):**

- Team focuses on "happy path"
- "We've done similar before, will be quick"
- Complexity underestimation is a natural cognitive error

**Step Estimation (realism):**

- Detailing forces thinking about problems
- "What if...", "Need to consider..."
- Discovery of hidden complexities

**Balance:**
Optimistic estimation at Refinement → fast backlog planning
Pessimistic estimation at Step Estimation → realistic sprint planning

---

## Approach Benefits

### 1. **Improved Estimation Accuracy**

- Detailing reveals hidden subtasks at planning stage
- Accumulates knowledge base about real effort of typical steps
- Reduces impact of optimism and cognitive biases

### 2. **Better Sprint Planning**

- Ability to parallelize independent steps
- Project critical path identification
- More even team loading

### 3. **Structured Retrospective** _(optional)_

- Concrete data instead of subjective feelings
- Identification of systemic process problems
- Material for improving future estimations

### 4. **Risk Reduction**

- Early identification of task dependencies
- Prevention of "forgotten" steps
- Ability for early replanning when deviations occur

### 5. **Progress Transparency**

- Early identification of blockers and problems

### 6. **Preliminary Test Coverage Assessment**

- Surface-level estimate of required unit tests volume
- Planning testing effort at estimation stage

---

## Process Organization

### Refinement Session (main)

**Goal:** Initial backlog task estimation

**Participants:** Entire development team

**Process:**

1. Product Owner presents task
2. Acceptance Criteria discussion
3. Clarifying questions
4. Estimation through agile poker (Planning Poker)
5. Recording estimate in story points

**Duration:** 1-2 hours

**Estimation Character:** Optimistic, fast, high-level

### Step Estimation Session (additional)

**Goal:** Detailed decomposition of complex tasks

**Participants:**

- Required: developers who will work on the task
- Desirable: Tech Lead, QA Engineer
- Optional: Product Owner (for requirements clarification)

**Task Selection for Detailing:**
Team votes for tasks that need detailing:

- Tasks with intuitive uncertainty
- Tasks 5+ story points
- Tasks affecting critical components
- Tasks with technical risks (breaking changes, external integrations)
- Tasks where Refinement estimation caused disputes

**Process:**

1. Task selection for detailing (based on voting results)
2. Decomposition into Implementation Steps
3. Estimation of required test quantity
4. Identification of dependencies between steps
5. Option to adjust initial estimate
6. Move to next task

**Duration:** 1-1.5 hours (3-5 tasks detailed)

**Frequency:** Once per sprint or as needed

**Estimation Character:** Pessimistic, detailed, realistic

---

## Practical Examples

### Example 1: Optimism vs Realism Effect

**Task:** "Add two-factor authentication"

**Refinement (optimistic estimate):**

```
Discussion (5 minutes):
Dev 1: "Need to add database field, create form, connect TOTP library"
Dev 2: "Yeah, sounds like a medium task"
Dev 3: "We've done similar with email confirmation"
PO: "Acceptance Criteria are simple: enable, disable, use at login"

Voting: 5, 5, 5, 8
Consensus: 5 SP

Thinking: "Main functionality is clear, library will do everything"
```

**Step Estimation (pessimistic estimate):**

```
Detailing (20 minutes):

Implementation Steps:
1. Create migration for two_factor_secret field in users table
2. Add two_factor_enabled field (boolean)
3. Add enable2FA/disable2FA methods to User model
4. Install library for TOTP code generation
5. Study library documentation for edge cases
6. Create TwoFactorController controller
7. Implement QR code generation for setup
8. Add TOTP check at login in AuthController
9. Handle case when user lost device
10. Create backup code recovery system
11. Create UI for enabling/disabling 2FA
12. Create UI for showing QR code
13. Create UI for showing backup codes
14. Add rate limiting for code entry attempts
15. Write unit tests for User model (4 tests)
16. Write tests for TwoFactorController (5 tests)
17. Write tests for BackupCodeService (3 tests)
18. Write integration tests (3 tests)
19. Update API documentation
20. Test on different devices
21. Test integration with mobile applications

Tests: ~15 unit + 3 integration = 18 tests

Discussion:
Dev 1: "Oh, I forgot about backup codes in first estimate"
Dev 2: "And I didn't think about rate limiting either"
Dev 3: "Testing will take longer than I thought"
Tech Lead: "Plus need to consider security and edge cases"

Re-estimation: 5 SP → 8 SP

Thinking: "When you start detailing, you understand the real scope of work"
```

### Example 2: Correction After Detailing

**Task:** "Add report export to PDF and Excel"

**Refinement (optimistic):**

```
Team: "Libraries for PDF and Excel are ready-made,
just connect and add export button"

Estimate: 3 SP
```

**Step Estimation (pessimistic):**

```
Detailing revealed:

1. Library selection (research):
   - Compare 3 PDF libraries
   - Compare 2 Excel libraries
   - Check licenses

2. PDF export (8 steps):
   - Configure library
   - Configure fonts (beyond Latin)
   - Handle tables
   - Handle charts
   - Configure pagination
   - Add company styles (logo, colors)
   - Optimize file size
   - Tests (4 tests)

3. Excel export (6 steps):
   - Configure library
   - Export table data
   - Cell formatting
   - Formulas for total rows
   - Sheet protection
   - Tests (3 tests)

4. UI and integration (5 steps):
   - Add export buttons
   - Add format selection
   - Progress bar for large reports
   - Error handling
   - UI tests (2 tests)

5. Performance (3 steps):
   - Background generation for large files
   - Data size limits
   - Temporary file cleanup

6. Documentation and edge cases (3 steps):
   - Update user documentation
   - Testing with boundary data volumes
   - Testing with various browsers

Total: 25+ steps, 9+ tests

Discussion:
Dev: "Oh, I completely forgot about other languages in PDF..."
QA: "And how do we handle the situation with a million rows?"
Tech Lead: "Will need background processing, that's a separate task"

Decision: Split into 2 tasks:
- "PDF export" - 5 SP
- "Excel export" - 3 SP
Instead of initial 3 SP for everything
```

---

## Methodology Application Levels

SBE can be applied with varying degrees of detail depending on team needs:

### Basic Level (minimal implementation)

**What We Do:**

- Conduct Refinement + Step Estimation sessions
- Decompose tasks into concrete steps
- Analyze dependencies for parallelization
- Estimate required tests

**What We Get:**

- More accurate estimations
- Better sprint planning
- Predictability of testing volume
- Balance between Refinement optimism and Step Estimation realism

**Effort:** +10-15% planning time (additional 1.5 hours Step Estimation)

### Advanced Level (with retrospective)

**Additionally Do:**

- Compare plan with reality
- Analyze divergence patterns
- Create templates for typical tasks

**Additionally Get:**

- Continuous improvement of estimation accuracy
- Team knowledge base about typical tasks
- Identification of systemic process problems

**Additional Effort:** +5-10% time for retrospective

---

## Methodology Implementation

### Initial Stage (1-2 sprints) - Basic Level

**Organizational Changes:**

- Add Step Estimation session to team calendar (1-1.5 hours/sprint)
- Define criteria for task voting
- Create template for recording Implementation Steps

**Process:**

- Select 2-3 tasks for Step Estimation by voting
- Focus on decomposition and dependency analysis
- Estimate required test coverage
- Compare optimistic and pessimistic estimates

### Development (3-6 sprints) - Can Add Retrospective

- Expand number of detailed tasks (up to 5-7)
- Create templates for recurring task types
- _(Optional)_ Start collecting data: planned vs actual
- _(Optional)_ Analyze divergence patterns

---

## Return on Investment of Methodology

### Basic Level

**Investment:** +10-15% planning time (additional 1.5 hours Step Estimation)

**Return:**

- Reduction of overruns
- Improved test planning
- Increased deadline predictability

### Advanced Level

**Investment:** +15-25% time for planning and retrospective

**Return:**

- Additional reduction of overruns
- Continuous process improvement
- Team knowledge base accumulation
- Time reduction for similar tasks in future
