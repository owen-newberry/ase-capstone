# ase-capstone

## Project Description

This capstone investigates what makes games actually compatible with modern GPU upscaling (DLSS, FSR) and frame generation. I'm building a game prototype to apply and validate specific architectural patterns identified through research.

The problem is straightforward: upscaling tech like DLSS and FSR are everywhere now, but there's surprisingly little concrete guidance on how to structure your code so they actually work well. Student and indie projects constantly break temporal reconstruction without realizing it—bad frame pacing, inconsistent motion vectors, unstable simulation logic.

I'm implementing three core patterns (fixed-timestep simulation, workload budgeting, temporal coherence) identified in my research paper and measuring their real-world performance. The game creates realistic stress conditions with AI workloads and environmental effects, making it a good test bed.

Deliverables: research paper analyzing GPU hardware's impact on game architecture, working game prototype demonstrating the patterns, and performance data validating the approach.

---

## Problem Domain

Temporal upscaling (DLSS, FSR) and frame generation are pretty much standard now for hitting high frame rates, but they make assumptions about how your code works:

- **Stable frame pacing** — consistent frame-to-frame timing
- **Coherent motion vectors** — predictable object movement
- **Temporal continuity** — deterministic simulation that doesn't change behavior at different frame rates

Break these assumptions and you get ghosting, smearing, stuttering, and other visual garbage. Common culprits: tying game logic directly to frame rate, having multiple systems fight over object transforms, or using frame counters instead of actual time.

Questions this project answers:

- How do specific architectural patterns support upscaler compatibility?
- What's the measurable performance impact of implementing these patterns?
- Can you validate this stuff in a real game context instead of just theory?

I'm implementing patterns identified through research to demonstrate their practical application.

---

## Features & Requirements

### Feature 1: Fixed-Timestep Simulation Pattern

| ID | User Story |
|----|------------|
| F1.1 | As a developer, I should separate simulation tick from render frame |
| F1.2 | As a system, simulation should produce deterministic output |
| F1.3 | As a developer, I should interpolate visual state between simulation ticks |
| F1.4 | As a developer, I should validate motion vector stability |

### Feature 2: Workload Budgeting System

| ID | User Story |
|----|------------|
| F2.1 | As a developer, I should implement per-frame AI time budgets |
| F2.2 | As a system, I should time-slice expensive AI operations |
| F2.3 | As a developer, I should prioritize AI tasks by importance |
| F2.4 | As a system, I should defer non-critical AI work when under load |
| F2.5 | As a developer, I should log budget usage and overruns |
| F2.6 | As a developer, I should measure frame-time stability improvement |

### Feature 3: Temporal Coherence Patterns

| ID | User Story |
|----|------------|
| F3.1 | As a developer, I should implement single-writer motion authority |
| F3.2 | As a system, motion vectors should remain coherent across frames |
| F3.3 | As a developer, I should convert effects to time-based updates |
| F3.4 | As a system, I should produce deterministic visual output |

### Feature 4: Performance Measurement Framework

| ID | User Story |
|----|------------|
| F4.1 | As a developer, I should collect frame-time metrics |
| F4.2 | As a developer, I should measure CPU/GPU utilization |
| F4.3 | As a developer, I should track memory usage and allocation patterns |
| F4.4 | As a developer, I should track 1% low and 0.1% low FPS |
| F4.5 | As a developer, I should export performance data for analysis |
| F4.6 | As a system, I should generate automated performance reports |

### Feature 5: DLSS/FSR Integration and Validation

| ID | User Story |
|----|------------|
| F5.1 | As a developer, I should integrate DLSS and/or FSR into the prototype |
| F5.2 | As a developer, I should test all patterns with upscaling enabled |
| F5.3 | As a system, I should measure upscaling performance impact |
| F5.4 | As a developer, I should validate visual quality and temporal stability |

### Feature 6: Game Prototype (Stress-Test Context)

| ID | User Story |
|----|------------|
| F6.1 | As a developer, I should create a confined test environment |
| F6.2 | As a developer, I should implement player movement and interaction |
| F6.3 | As a developer, I should add AI entity with variable workload |
| F6.4 | As a developer, I should include environmental effects for testing |

---

## Project Documentation

- [Project Plan Presentation](https://github.com/owen-newberry/ase-capstone/blob/main/docs/PPP/pdf/ppp.pdf)

---

## Schedule & Milestones

**Two-part capstone:**
1. **Research Paper** — How GPU advancements (especially AI-focused hardware like Blackwell) are changing game development workflows and architecture patterns
2. **Code Project** — Building and testing those patterns in a real game

### Sprint 1 (4 weeks) — Research Paper Completion
**Start Date:** February 2, 2026  
**Primary Deliverable:** Initial research phase including literature review, case study analysis, and theoretical framework development

**Research Focus:**
- How GPU advancements (Blackwell architecture, AI integration) reshape game development
- Software engineering pattern evolution in response to hardware changes
- Impact of AI-driven rendering (DLSS, FSR, frame generation) on development workflows
- Analysis of modern game engines (Unreal Engine 5, Unity) adapting to new GPU capabilities

### Sprint 1 (4 weeks) — Research Paper Completion
**Start Date:** February 2, 2026  
**Primary Deliverable:** Complete research paper

**Research Work (Priority):**

**Week 1 (Feb 2-8): Historical and Technical Foundation**
- Survey academic and industry literature on GPU evolution
- Establish architectural inflection points in gaming hardware
- Document traditional rendering pipelines vs. AI-integrated approaches
- Read Nvidia Blackwell and Ada Lovelace technical documentation
- Begin drafting introduction section

**Week 2 (Feb 9-15): Case Study Analysis & Writing**
- Unreal Engine 5 (Lumen/Nanite architecture) documentation deep-dive
- Unity's ECS/DOTS framework for parallel processing analysis
- DLSS/FSR technical implementation and SDK documentation
- Watch GDC talks on modern engine architecture
- Write methodology section and begin case study analysis sections

**Week 3 (Feb 16-22): Blackwell Deep Dive & Synthesis**
- Nvidia Blackwell technical documentation and SDK analysis
- Ray tracing vs. rasterization performance implications research
- Neural rendering and frame generation impact on software design
- Benchmark analysis and performance comparisons
- Write findings and analysis sections
- Draft conclusions

**Week 4 (Feb 23-29): Writing, Revision & Finalization**
- Identify recurring engineering patterns from research
- Connect hardware capabilities to software design decisions
- Complete all sections of research paper
- Comprehensive revision and editing
- Finalize bibliography and citations
- Proofread and format final paper
- Submit completed research paper

**Code Preparation:**

**Weeks 1-4:**
- Engine selection based on research findings
- Install engine and familiarize with tools (minimal time)
- Review DLSS/FSR SDK documentation (supports research)
- Plan project architecture (can inform paper)

### Sprint 2 (6 weeks) — Code Implementation & Validation
**Start Date:** March 16, 2026
**Primary Deliverable:** Working game prototype implementing validated architectural patterns with performance analysis

**Phase 1: Core Pattern Implementation (Weeks 1-3 — Mar 2-22)**
**Features: F1.1-F1.5, F2.1-F2.5, F3.1-F3.5, F6.1-F6.2**

- Set up project structure and version control
- Create test environment (Feature F6.1)
- Implement basic player movement and interaction (Feature F6.2)
- Implement fixed-timestep simulation (Features F1.1-F1.3)
- Add workload budgeting system (Features F2.1-F2.4)
- Implement temporal coherence patterns (Features F3.1-F3.3)
- Set up performance profiling tools (Feature F4.1)
- Measure pattern performance (Features F1.4-F1.5, F2.5, F3.4-F3.5)

**Phase 2: DLSS/FSR Integration (Weeks 4-5 — Mar 23-Apr 5)**
**Features: F4.2-F4.5, F5.1-F5.5, F6.3-F6.4**

- Integrate DLSS and/or FSR (Feature F5.1)
- Test all patterns with upscaling enabled (Feature F5.2)
- Complete AI entity with variable workload (Feature F6.3)
- Add environmental effects for temporal testing (Feature F6.4)
- Complete performance measurement framework (Features F4.2-F4.5)
- Measure upscaling performance impact (Feature F5.3)
- Capture visual quality data (Features F5.4-F5.5)

**Phase 3: Validation & Documentation (Week 6 — Apr 6-12)**
**Features: F6.5**

- Stress-test all patterns with full prototype (Feature F6.5)
- Run comprehensive performance tests
- Generate performance graphs and analysis
- Create system architecture diagrams
- Write implementation guide documenting patterns
- Prepare presentation materials

**Final Deliverables (End of Sprint 2):**
- Working game prototype demonstrating all patterns
- Performance analysis report
- Implementation guide documenting patterns
- System architecture diagrams
- Presentation materials

---