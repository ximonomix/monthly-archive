# Resonant Knowledge Archive — October 2026

*A subject-based archive of discussions, experiments, technical demonstrations and community learning.*  
**Coverage:** 1–31 October 2026 · **Edition:** 3.0 · **Updated:** 7 November 2026

> **Reading guide:** This archive synthesises supplied meeting summaries and chats, selected Discord messages and user-provided YouTube chapter information. **Reported** and **demonstrated** describe what participants said or showed; **proposed** refers to plans; **unresolved** means the source does not establish an answer. Model and legal claims are historical October 2026 discussions, not current independent verification. Recording links and Discord originals support follow-up; private recordings are not linked publicly.

## Contents

1. [Local AI hardware and infrastructure](#1-local-ai-hardware-and-infrastructure)
2. [Models, inference and evaluation](#2-models-inference-and-evaluation)
3. [Agents, harnesses and automation](#3-agents-harnesses-and-automation)
4. [Memory, knowledge and retrieval](#4-memory-knowledge-and-retrieval)
5. [Creative AI and media production](#5-creative-ai-and-media-production)
6. [ResonantOS, DAO and governance](#6-resonantos-dao-and-governance)
7. [AI literacy, education and human development](#7-ai-literacy-education-and-human-development)
8. [Security, ethics and digital rights](#8-security-ethics-and-digital-rights)
9. [Community practice and collaborative development](#9-community-practice-and-collaborative-development)
10. [Project index](#10-project-index)
11. [Sources, method and coverage](#11-sources-method-and-coverage)
12. [Public recording and chapter index](#12-public-recording-and-chapter-index)
13. [Editorial maintenance](#13-editorial-maintenance)

---

## 1. Local AI hardware and infrastructure

**October 21 and 28 updates.** Participants compared an RX 6800 with used RTX 3060/3090 cards for mid-sized Qwen models and considered how memory quantisation changes what fits in VRAM. The 28 October meeting contrasted CUDA systems, Apple Silicon and GPU offloading, while the 27 October Academy AMA examined **two RTX 3060 12 GB cards** as a budget learning configuration. [GPU choices (21 Oct, 20:45)](https://youtu.be/5_y9nyD72c0?t=1245) · [VRAM/RAM/NVMe tiers (27 Oct, 10:10)](https://youtu.be/iaIoTd38WdU?t=610) · [Used GPU discussion (28 Oct, 27:25)](https://youtu.be/lfFMutGNdi0?t=1645).

**Reported, not independently benchmarked:** An edited October 28 news segment described MoE-routing optimisations and a GPU prefill workaround with substantial speedups. Model size, quantisation, resident experts and workload must be recorded before treating those figures as comparable. [Strata explanation](https://youtu.be/bQ27yH0hggs?t=0) · [Tensor Core workaround](https://youtu.be/bQ27yH0hggs?t=977). Another edited Sunday Co-Op excerpt describes a dual Blackwell 6000 / RTX 5090 workstation and its power/heat constraints; the session date was not established in the supplied description. [Community hardware example](https://youtu.be/Cv6n_-yPLVg?t=24).


### What the community explored

Across four Wednesday **AI Stack** sessions and an active `local-hardware-lab` channel, the recurring question was not simply *which GPU is fastest?* but *which configuration delivers useful inference for a particular workload and budget?* The discussions considered consumer Nvidia cards, AMD Strix Halo systems, Apple Silicon, used enterprise GPUs, small machines, multi-GPU setups and more elaborate homelabs. Participants repeatedly distinguished **model capacity**, **prompt processing/prefill speed**, **generation speed**, **concurrency**, **power/thermal limits**, and **purchase cost**. These are different constraints; improving one need not improve the others.

**Reported practice — asymmetric offloading.** An October 3 Discord post described a Strix Halo plus external mobile GPU configuration that keeps active model components in a faster memory pool while offloading other components to unified memory. The author argued this could work better for their mixture-of-experts workloads than splitting everything evenly. This is a specific user-reported configuration, **not** a general performance result. [Original discussion](https://discord.com/channels/1423225702135894111/1517639386215350424/1555798102122954823).

**Reported experiment — old hardware and Strata.** On October 30, a member reported **40 tokens/s** for one quantised model distributed over CPU, RAM and a 16 GB V100, versus **34 tokens/s** for a different model running in VRAM on the same GPU. Model size and quantisation differed, so this is a useful case study in tuning rather than a controlled head-to-head benchmark. [Original report](https://discord.com/channels/1423225702135894111/1491424406595964958/1565849381775610111).

**Thermal design matters.** On October 1, members discussed blower-style cards, exhaust paths and heatsink fin orientation in closely packed systems. This illustrates how local AI performance depends on practical system engineering, not only model and GPU specifications. [Cooling discussion](https://discord.com/channels/1423225702135894111/1517639386215350424/1555093730392940668).

**Market observations are time-specific.** Discord discussions compared rapidly changing European prices and second-hand hardware; meeting summaries also explored the trade-offs of enterprise cards versus multiple consumer GPUs. Retain purchase dates and regions when citing such comparisons. [European pricing discussion](https://discord.com/channels/1423225702135894111/1517639386215350424/1555074692300279839).

**Open questions:** Which workloads merit extra VRAM rather than extra compute? How should beginners compare total system cost against cloud subscriptions? How reproducible are offloading gains across models, quantisations and inference engines?

**Meeting sources:** `AI Stack 2026 10 07.docx`; `AI Stack 2026 10 14.docx`; `AI Stack 2026 10 21.docx`; `AI Stack 2026 10 28.docx`.  
**Related:** [Models and evaluation](#2-models-inference-and-evaluation), [Agents and automation](#3-agents-harnesses-and-automation).

## 2. Models, inference and evaluation

**Strata and model-release reporting.** October 21 discussions included Strata v0.2 and hardware tests, Reflection AI’s Beam 1.0, small/fast models and audio generation. On October 28, Chris’s digest covered MoE routing, Desa speech generation, Flint coding and MOSS layout controls. Treat quoted release specifications and performance as **claims presented in October**, not as an independently checked product catalogue. [Strata benchmarks](https://youtu.be/5_y9nyD72c0?t=2665) · [Beam discussion](https://youtu.be/5_y9nyD72c0?t=3160) · [Edited 28 Oct digest](https://youtu.be/bQ27yH0hggs).

**Learning resource:** The October 6 evaluation workshop demonstrates rubrics, holdout sets, LLM judges, variability and regression testing. [Failure-mode example](https://youtu.be/kC3p2LCUPlg?t=375) · [Judge consistency](https://youtu.be/kC3p2LCUPlg?t=2030) · [Holdout data](https://youtu.be/kC3p2LCUPlg?t=3245).


### Models are not interchangeable benchmarks

The October AI Stack documents tracked model releases and comparisons, including Qwen variants, MiniMax, GLM, Kimi, audio models and inference tools. Community discussions compared open weights with hosted models and considered quantisation, context handling, KV caching, prefill and generation. Model-release names and roadmaps in the meeting documents are **contemporaneous reports**, not verified current catalogues.

### Moving from impressive demos to tests

An **Academy session on October 6** demonstrated a practical methodology for evaluating an AI workflow. A story-generation example deliberately gave characters restricted knowledge; an initial output leaked information that should have stayed secret. The session used the failure to show why evaluations should begin with a clearly defined expected behaviour, followed by **simple deterministic checks**, test cases that vary relevant inputs, and, when necessary, model-based judges. A judge is not a substitute for a well-defined test or independent validation.

A useful process emerging from the session:

1. State what the agent is meant to do and what failure looks like.
2. Create simple pass/fail checks for observable constraints.
3. Add broader cases and holdouts to avoid tuning only to one example.
4. Use an LLM judge for criteria that cannot be reduced to exact matches, and assess the judge's own consistency.
5. Track changes between versions, rather than declaring success from a single impressive run.

The October 20 Academy discussion also addressed the probabilistic nature of language models and the risk of plausible but unsupported answers. One participant reported a **42% drift rate in their own prior tests**; it must **not** be generalised to all models or uses. The description of LLM reasoning as *pretend reasoning* was a speaker's interpretation, not a verified conclusion about cognition.

**Open questions:** What minimum evidence should accompany shared model-performance claims? Can evaluation criteria survive changes in models and harnesses? Which reliability tests should be common across community projects?

**Meeting sources:** `Academy 2026 10 06 Keri Evaluating and Benchmarking.docx` (in this wiki, the presenter is referred to as *a member*); `ResonantDAO Academy 2026 10 20.docx`; AI Stack documents, 7–28 October.  
**Related:** [Local hardware](#1-local-ai-hardware-and-infrastructure), [Security](#8-security-ethics-and-digital-rights).

## 3. Agents, harnesses and automation

**Three reusable Academy demonstrations (20 October).** A focused explanation distinguishes models from harnesses; a demonstration inspects what an experimental agent sends in its context window and discusses sandbox permissions; an OpenCode Desktop tutorial shows installation, choosing models, isolating project folders and configuring web search. These are **edited excerpts of one Academy meeting**, not three additional meetings. [Model versus harness](https://youtu.be/T-ia3p6BOI0?t=262) · [Agent context inspection](https://youtu.be/p3KBOgxTd_E?t=75) · [OpenCode project folders](https://youtu.be/BcRfRs3_XBI?t=253).

**Current project demonstrations in October:** On October 16, Iron Jarvis was shown with local-only routing and UI controls, while Cyber Alchemy Lab presented authority, provenance and lifecycle boundaries for agent systems. These were demonstrations and proposals, not independent production-readiness assessments. [Iron Jarvis](https://youtu.be/sLQLyts4Vko?t=248) · [Cyber Alchemy’s three lenses](https://youtu.be/sLQLyts4Vko?t=2257).


### Distinguishing the components

A useful conceptual distinction from the **October 20 Academy** session was between the **model** (generates responses), the **harness** (interface, tools, execution, conversations and orchestration), and **external state or memory** (persisted and retrieved outside a model's active context). This distinction helps diagnose whether a problem arises from model capability, tool permissions, workflow design or missing context.

The **October 9 Project Showcase** compared Hermes, Pi and other agent approaches; the AI Stack calls discussed Hermes, LM Studio, OpenCode, DeepSeek-related harnesses and inference engines. These were community assessments tied to specific versions and personal workloads. They should not be read as a permanent ranking.

**Beginner pathway.** A member seeking a first local agent on October 1 received suggestions to begin with a simpler local model interface before adding a more complex harness. This was practical advice about learning in manageable stages rather than a claim that one platform fits everyone. [Question](https://discord.com/channels/1423225702135894111/1423225703637323830/1555027448188502089) · [Response](https://discord.com/channels/1423225702135894111/1423225703637323830/1555048502084501588).

**Permissions and isolation.** A member experimenting with Hermes in a restricted TrueNAS container questioned whether agents within a shared instance could genuinely maintain separate access to credentials and MCP services. The post usefully separates UI-level profiles from operating-system/container-level security boundaries. It is a reported design concern, not an independently audited vulnerability. [Harness security discussion](https://discord.com/channels/1423225702135894111/1546522589852340280/1558079042065006603).

**Resumability and durable workflows.** The **October 16 Project Showcase** reported features in Iron Jarvis for project folder tracking, local model use, UI outputs and recovery after interruption. The **October 31 ResonantOS alpha update** reported agent switching in a demo shell, support for starting a harness without an additional plugin, and further extension integration in progress. Treat the update's **shipped / in progress / next** distinctions literally. [ResonantOS update](https://discord.com/channels/1423225702135894111/1423225703637323830/1565924723370754132).

**Open questions:** What constitutes effective privilege separation between agents? When should a process be deterministic rather than agent-directed? How should long-running tasks expose their state, approvals and failures?

**Meeting sources:** `Friday Project Showcase 2026 10 09.docx`; `Friday Project Showcase 2026 10 16.docx`; `ResonantDAO Academy 2026 10 20.docx`; AI Stack documents.  
**Related:** [Memory and retrieval](#4-memory-knowledge-and-retrieval), [Security](#8-security-ethics-and-digital-rights).

## 4. Memory, knowledge and retrieval

**Context versus persistence.** The 20 October Academy conversation separated the model’s active input context from records kept outside the model. A member’s *company brain* concept on 16 October added a further distinction: authority over definitions, provenance of claims and states through which work moves. Whether these structures measurably improve recall remains open. [Working versus long-term memory](https://youtu.be/Gnq1l3ZlDGA?t=835) · [Company brain and evolving definitions](https://youtu.be/sLQLyts4Vko?t=2880) · [RAG and embedding models](https://youtu.be/5_y9nyD72c0?t=7255).


### Context is not durable knowledge

The October 20 Academy explained that a context window represents information available during a particular model response. Persisted notes, source files and databases only help if a system **stores and retrieves** the relevant information for a later task. This is why an agent may appear to remember a conversation in one setting but lose essential facts when its active context changes.

**Practical retrieval design.** An October 1 Discord exchange on searching thousands of images proposed classifying or summarising each image once, then searching that searchable description rather than re-analysing every image for every query. Members also noted that the right classification fields depend on the questions users are likely to ask: an overly shallow index misses details, while an excessively specific one can be costly to maintain. [Discussion on preprocessing](https://discord.com/channels/1423225702135894111/1423225703637323830/1555009587080462399) · [Discussion on classification depth](https://discord.com/channels/1423225702135894111/1423225703637323830/1555010871846240448).

**Search versus a functioning knowledge graph.** On October 24, the developer of a memory project explained that local keyword/semantic search, version tracking and retired-note handling had been implemented, but intended graph behaviour—links strengthening through use, spreading recall and discovery of relationships—had **not** yet been built. This is a valuable distinction between an implemented retrieval layer and a proposed memory architecture. The author described plans to benchmark the missing layer before deployment; results were not established by that message. [Project status and limitations](https://discord.com/channels/1423225702135894111/1423225703637323830/1563389288387715115).

The **October 16 Project Showcase** introduced an AI governance/knowledge framework arranged around **Authority** (what is valid or within scope), **Provenance** (where an assertion or record came from), and **Life Cycle** (how it changes over time). These lenses are relevant to knowledge archives themselves: a useful entry should have traceable origins, a dated interpretation and an update path.

**Open questions:** How can retrieval return not just relevant text but its date, authority and superseded status? What tests demonstrate that a graph improves recall? Who can correct or remove a stored personal fact?

**Meeting sources:** `ResonantDAO Academy 2026 10 20.docx`; `Friday Project Showcase 2026 10 16.docx`; `Coding Academy 2026 10 04.docx`.  
**Related:** [Agents](#3-agents-harnesses-and-automation), [Community practice](#9-community-practice-and-collaborative-development).

## 5. Creative AI and media production

**Workflows across three labs.** The 12 October lab examined a music-video pipeline that combined Suno, still imagery, animation and code-based effects. The 19 October session explored FFmpeg-driven editing and discussed licensing, commercial use and voice cloning. On 26 October, a corridor-chase experiment revealed style drift and unwanted storyboard marks, leading to a practical recommendation to generate more takes and edit selectively. [Video assembly (12 Oct, 24:45)](https://youtu.be/A7sIYEGmMI8?t=1485) · [Automated editing (19 Oct, 06:17)](https://youtu.be/3hMbjGMkv4s?t=377) · [Storyboarding test (26 Oct, 21:35)](https://youtu.be/V6INncVVdco?t=1295).


### Workflow matters as much as generation

The **Creative AI Video Lab** sessions on **October 12, 19 and 26** documented experiments across music generation, video generation, scripted editing, audio synchronisation and multi-tool workflows. The October 12 discussion of *slopcore* music videos distinguished the appealing story of autonomous overnight generation from the actual work of guiding outputs, revising prompts, tracking API costs, selecting assets and correcting timing. The October 19 materials discussed FFmpeg/Claude-style pipelines, licensing, voice work and practical editorial judgement.

A detailed **October 27 Discord breakdown** illustrates a reproducible production pattern: locally transcribe a community meeting with two speech-recognition models; reconcile names; extract takeaways; compose original lyrics and audio; generate character visuals; assemble animation in code; render with a browser and FFmpeg; watch, annotate and correct. The author explicitly described **human review between iterations** rather than a fully autonomous pipeline. [Ten-step production workflow](https://discord.com/channels/1423225702135894111/1544435111934566460/1564764357596811299).

The `video-generation` channel also included feedback on cuts, sound levels, visual continuity and sharing methods. These exchanges show why the craft of direction and editing remains relevant even when individual assets are machine-generated. A later October 31 post shared a ComfyUI workflow for producing images in a reference style, explicitly crediting another community as its origin. [Workflow sharing](https://discord.com/channels/1423225702135894111/1544435111934566460/1565881768932810752).

**Rights and provenance:** Creative experiments often combine generated media, uploaded references, commercial tools and community assets. The archive should distinguish *what the creator reports using* from *what rights are established*. A public example is not itself evidence of a licence to reuse every component.

**Open questions:** How should projects record tools, costs and prompts in a portable format? How can creators attribute contributions and source assets? Which parts of an agent-driven production pipeline merit manual review?

**Meeting sources:** `Creative AI Video Lab 2026 10 12.docx`; `Creative AI Video Lab 2026 10 19.docx`; `Creative AI Video Lab 2026 10 26.docx`.  
**Related:** [Education](#7-ai-literacy-education-and-human-development), [Rights](#8-security-ethics-and-digital-rights).

## 6. ResonantOS, DAO and governance

**Contribution economy development.** On October 12, Victor presented a proposed 22-dimension contribution model and workflows for capturing actions and evidence. An edited short makes its concepts accessible separately from the full discussion. The October 26 update described feed, custodian, bounty and group-work UI, and experimental CRABS and EOTH cryptographic schemes. The descriptions establish *what was shown or proposed*, not that the security designs were audited or production ready. [Full 12 Oct meeting](https://youtu.be/0PRtiGZS2KE?t=375) · [12 Oct short: 22 dimensions](https://youtu.be/ar9FzY990q8?t=167) · [26 Oct: bounties and tribes](https://youtu.be/6quDsU24xEI?t=374) · [26 Oct: experimental cryptographic protocols](https://youtu.be/6quDsU24xEI?t=1476).


### Contribution rather than simple capital ownership

The two October 12 DAO Exploration documents present a **proposed** community-of-communities model in which participation and contribution would affect reputation, governance and potential economic benefit. A described design maps contributions across **22 archetypal dimensions**; prototypes, interfaces, proof-of-contribution records and Solana-based components were discussed as part of the roadmap. The meeting also explored a proposed multi-token economy. These details describe aspirations and works in progress, **not evidence that the complete governance or token system was deployed**.

### A recurring disagreement: local software versus collective ownership

The **October 23 Project Showcase**, split into two supplied parts, generated a substantive debate around the Everywhere/Everywear project and plans for a later decentralised ecosystem. One perspective defended a founder-led business selling proprietary software and orchestration while allowing users to retain ownership of their hardware and local models. Another argued that keeping platform ownership and economic decision-making centralised is materially different from a genuinely co-owned DAO. These are distinguishable governance models, not merely a disagreement over terminology.

The discussion continued on Discord. In an October 30 post, the developer clarified the distinction between user-owned compute, free applications and paid proprietary orchestration, and described a proposed investment valuation and future roadmap. These remain **developer statements and projections**, not verified business valuation or completed architecture. [Original clarification](https://discord.com/channels/1423225702135894111/1423225703637323830/1565664350536990772).

**ResonantOS technical progress.** A separate October 31 alpha update reported functioning harness switching in a demonstration shell and further browser-extension integration under development. This product update should not be conflated with the DAO's contribution-token roadmap. [Alpha status](https://discord.com/channels/1423225702135894111/1423225703637323830/1565924723370754132).

**Open questions:** Who owns intellectual property generated by collaborative development? How does a contribution earn decision rights? Can contributor reputation be contested, corrected or withdrawn? What would make a system substantively decentralised rather than decentralised only in infrastructure?

**Meeting sources:** `ResonantDAO Exploration 2026 10 12.docx`; `Resonant DAO Exploration and Community Sync 2026 10 12.docx` (overlapping accounts of the same date); `Friday Project Showcase 2026 10 23 P1.docx`; `Friday Project Showcase 2026 10 23 P2.docx`.  
**Related:** [Local AI](#1-local-ai-hardware-and-infrastructure), [Community practice](#9-community-practice-and-collaborative-development).

## 7. AI literacy, education and human development

**Human judgement and access.** The October 1 Augmented Minds discussion framed domain expertise, taste and lived experience as contributions that cannot be reduced to using an AI tool. The October 8 discussion contrasted deterministic and open-ended problems, including empathy and boundaries of proposed AI solutions. The October 30 showcase described visits to more than 25 US libraries and considered the advantages of structured research, unexpected discovery and a clearer learning sequence. [Human uniqueness (1 Oct, 02:03)](https://youtu.be/ffHwyV0K0Ik?t=123) · [Problem-solving approaches (8 Oct, 18:35)](https://youtu.be/Ro_8oRycSkE?t=1115) · [Library study (30 Oct, 24:17)](https://youtu.be/tTa1sAl3k_o?t=1457).


### Learning to use AI without surrendering judgement

The **October 1 Augmented Minds** discussion questioned what makes human work distinctive as AI tools become widely available. Participants emphasised domain experience, judgement, taste, relationships and the capacity to frame worthwhile problems. The *talent tree* metaphor described the changing relationship between conventional career progressions and faster AI-assisted experimentation. These were interpretations of social change, not a verified forecast of employment outcomes.

The **October 8 Augmented Minds** discussion moved through problem-solving, empathy, deterministic versus open-ended tasks, and different conceptions of human values. It did not arrive at a single position on AI cognition or future social effects; preserve that plurality.

**From philosophy to introductory teaching.** A Discord post on October 18 sought to design a genuine beginner sequence rather than simply instructing people to create an account. Replies suggested basic vocabulary (models, tokens, quantisation), creative applications, AI as a tutor and the importance of human ethical guidance. These are proposals for curriculum design, not established learning-outcome evidence. [Beginner curriculum question](https://discord.com/channels/1423225702135894111/1543996880441180240/1561474780127961219) · [Suggested foundations](https://discord.com/channels/1423225702135894111/1543996880441180240/1561484340884668588).

**Libraries and discovery.** In the **October 30 Project Showcase**, a presenter reported visits to more than 25 public and academic libraries and argued that physical browsing can surface unexpected connections and historical context absent from prompt-driven search. The useful educational distinction is between having many tools available and developing a **sequence for learning**. The library observations are the presenter's field reports, not a systematic survey of US libraries.

**Open questions:** Which AI concepts should all beginners understand before using autonomous tools? How can teaching distinguish confident answers from defensible evidence? Can communities build learning pathways that encourage creativity while maintaining critical evaluation?

**Meeting sources:** `Augmented Minds 2026 10 01.docx`; `Augmented Minds 2026 10 08.docx`; `Coding Academy 2026 10 04.docx`; `Friday Project Showcase 2026 10 30.docx`.  
**Related:** [Models and evaluation](#2-models-inference-and-evaluation), [Knowledge and retrieval](#4-memory-knowledge-and-retrieval).

## 8. Security, ethics and digital rights

**Specific October questions.** The archive distinguishes local deployment from actual isolation, and privacy intentions from verified safeguards. The Academy OpenCode tutorial recommends isolated working folders; the experimental Augmentor demonstration discusses agent permissions. The October 19 creative lab considered licensing and voice identity. The October 27 Academy AMA discussed open-source licensing compliance and community expectations; specific accusations from that exchange are not treated as established facts. [Agent permissions](https://youtu.be/p3KBOgxTd_E?t=305) · [OpenCode account privacy](https://youtu.be/BcRfRs3_XBI?t=175) · [Media licences (19 Oct)](https://youtu.be/3hMbjGMkv4s?t=1442) · [Licensing and DAO values (27 Oct)](https://youtu.be/iaIoTd38WdU?t=1630).


### A local model does not automatically make an agent safe

Security emerged as a practical systems question across `general`, `harnesscraft`, `security-and-privacy` and the meeting discussions: Where does executable code come from? Which keys and files can an agent access? Can tools reach the network? Are different agents actually isolated? How are browser or extension permissions constrained?

On **October 2**, a member shared an external report about malicious code distributed through a seemingly legitimate model repository. The post recommended checking provenance, official sources and model-card discussion, and warned that add-on skills can widen the attack surface. The incident details were relayed through a summary and **have not been independently verified in this archive**. [Source discussion](https://discord.com/channels/1423225702135894111/1423225703637323830/1555587330683969688).

On **October 9**, a separate member raised the concern that multiple agent profiles under one user account might not provide meaningful credential isolation. That observation supports a broader design principle: *do not confuse an application label or role with an enforced security boundary*. [Original concern](https://discord.com/channels/1423225702135894111/1546522589852340280/1558079042065006603).

A **October 27** message circulated a detailed, time-sensitive claim about an SSH privilege-escalation issue affecting specified networking-tool versions and discussed mitigations. Because vulnerability status can change quickly, it should be preserved as a **historical alert**, not presented as a current unpatched advisory. [Historical security alert](https://discord.com/channels/1423225702135894111/1423225703637323830/1564635394870349930).

Ethical and policy exchanges also touched on AI export controls, EU regulation, watermarking, model access, copyright and whether local access increases individual autonomy. Some participants challenged exaggerated interpretations of proposed rules; without the actual legal text and jurisdiction-specific review, these should remain **discussion claims**, not legal advice.

**Open questions:** What permissions should beginner agents have by default? What counts as independent verification of model and extension sources? How can users retain control over stored personal information? How should the community distinguish urgent security information from unverified alerts?

**Meeting sources:** `AI Stack 2026 10 07.docx`; `AI Stack 2026 10 21.docx`; `Friday Project Showcase 2026 10 09.docx`; `Creative AI Video Lab 2026 10 19.docx`; `Augmented Minds 2026 10 08.docx`.  
**Related:** [Agents](#3-agents-harnesses-and-automation), [Creative media](#5-creative-ai-and-media-production).

## 9. Community practice and collaborative development

**From discussion to usable records.** The archive connects experiments, questions and project demonstrations across channels rather than counting meetings as isolated outputs. On October 2, a project showcase combined AI fundamentals with a 3D facility-modelling demonstration; on October 9, participants compared harnesses and discussed agents, memory and human oversight. The October 30 library presentation proposed more reproducible, shared research methods. [3D facility demo (2 Oct)](https://youtu.be/pN1OKmuPR_E?t=2250) · [Harness comparisons (9 Oct)](https://youtu.be/BWcljSnAwgw?t=2620) · [Library research framework (30 Oct)](https://youtu.be/tTa1sAl3k_o?t=3930).


### The value of people alongside tools

The Discord corpus demonstrates a recurring pattern of **questions, experiential replies, demonstrations, corrections and follow-up**. Members ask what to buy, share local benchmark figures, compare tools, flag potential risks and adapt each other's methods. The archive should preserve the *reasoning and useful outcome* of those exchanges rather than accumulate every message or rank contributors by posting volume.

One small exchange about image-search advice raised an interesting social question: someone asking peers for help may want experience, dialogue or a sense of community, not simply the fastest answer from a model. That distinction matters in an AI-focused space: automated answers and human communities serve overlapping but non-identical functions. [Discussion](https://discord.com/channels/1423225702135894111/1423225703637323830/1554985155108671509).

The recorded sessions supply a parallel learning environment. **Project Showcases** presented work in progress, from local agents and professional applications to business and governance experiments. **AI Stack** collected practical questions about system constraints. **Academy** and **Coding Academy** offered conceptual and methodological framing. **Creative AI Video Lab** documented iterative craft. Their value for an archive is greatest when connected across subjects, not stored as disconnected event summaries.

**Knowledge-sharing practice:** A strong contribution to this archive is one that identifies a problem, explains the attempted approach, records observations and limitations, and links to the original source. This is an editorial principle adopted for the archive, not a claim that every Discord message already meets that standard.

**Open questions:** Which Discord threads contain durable lessons, and which are transitory troubleshooting? How can corrections update older entries without erasing the discussion history? How can community knowledge remain accessible to non-technical newcomers?

**Meeting sources:** cross-cutting across all seven series; especially `Friday Project Showcase 2026 10 16.docx` and `Friday Project Showcase 2026 10 30.docx`.  
**Related:** [Education](#7-ai-literacy-education-and-human-development), [DAO governance](#6-resonantos-dao-and-governance).

## 10. Project index

This index points to projects **as described or demonstrated in October**, without implying that every feature was complete or independently tested.

| Project / initiative | October coverage | Primary topic | Evidence or further reading |
|---|---|---|---|
| **Strata / inference offloading** | Updates, configuration trade-offs, local performance reports | [Hardware](#1-local-ai-hardware-and-infrastructure) | AI Stack 7–28 Oct; [member configuration](https://discord.com/channels/1423225702135894111/1517639386215350424/1555798102122954823) |
| **Iron Jarvis** | Demonstrated agent functions, durable project state, local model modes | [Agents](#3-agents-harnesses-and-automation) | Project Showcase 16 Oct; [supplied repository](https://github.com/RealDealCPA-VR/Iron-Jarvis) |
| **Iron Books** | Described accounting-oriented application | [Agents](#3-agents-harnesses-and-automation) | Project Showcase 16 Oct; product status not independently tested |
| **Cyber Alchemy Lab** | Authority, provenance and life-cycle approach to multi-agent knowledge | [Knowledge](#4-memory-knowledge-and-retrieval) | Project Showcase 16 Oct; [supplied website](http://cyberalchemize.com/) |
| **Everywhere / Everywear and memory vault** | Founder-led local software vision, memory design, ownership dispute | [DAO](#6-resonantos-dao-and-governance) / [Memory](#4-memory-knowledge-and-retrieval) | Project Showcase 23 Oct Parts 1–2; [memory implementation disclosure](https://discord.com/channels/1423225702135894111/1423225703637323830/1563389288387715115) |
| **ResonantOS 2.0 alpha** | Harness-switching demo shell and development roadmap | [Agents](#3-agents-harnesses-and-automation) | [31 Oct status](https://discord.com/channels/1423225702135894111/1423225703637323830/1565924723370754132); [supplied repository](https://github.com/ResonantOS/2.0.0-alpha) |
| **DAO contribution model** | 22-dimensional contribution framework, ownership and token proposals | [DAO](#6-resonantos-dao-and-governance) | Two overlapping Exploration documents, 12 Oct |
| **Creative AI production pipelines** | Audio-to-video assembly, iterative editing, browser rendering | [Creative media](#5-creative-ai-and-media-production) | Video Lab 12–26 Oct; [27 Oct workflow](https://discord.com/channels/1423225702135894111/1544435111934566460/1564764357596811299) |
| **Industrial 3D simulation / automated bidding** | Project demonstrations and descriptions | [Agents](#3-agents-harnesses-and-automation) | Project Showcase meeting held 2 Oct (uploaded file formerly labelled 3 Oct) |
| **AI beginner curriculum** | Proposed beginner-first videos and core concepts | [Education](#7-ai-literacy-education-and-human-development) | [18 Oct discussion](https://discord.com/channels/1423225702135894111/1543996880441180240/1561474780127961219) |

---

## 11. Sources, method and coverage

This edition integrates the **October Discord export (4,309 messages)** with **17 latest public-meeting documents** and supplementary private-meeting notes. The two October 23 showcase parts are not linked publicly. October 12 DAO documentation has both a full-meeting record and a shorter, edited introduction; it is counted as **one meeting**, not two.

**Method.** Discussion themes are organised by subject rather than by call. Where a claim is contentious, time-sensitive, experimental or anecdotal, it is described as reported, demonstrated, discussed or proposed. YouTube chapter URLs point to the time positions supplied by the user or the uploaded DOCX; their contents were not re-transcribed or independently verified. Original Discord message URLs remain in the topic chapters.

**Discord boundaries.** The JSON covers the period **1–31 October 2026 (Europe/Madrid)** and selected channels plus accessible public threads; it does not include private threads, deleted messages, attachment contents or voice/video transcripts. The export is not a complete record of all community activity. Discord links may require membership.

**Recording availability.** Public source entries with a URL are directly linked below. The October 23 Project Showcase parts and the October 21 private AI Stack News video (#23 in the user’s list) are **excluded from the public video register**. Meeting notes can inform synthesis without exposing a private source. Additional video identifiers not matched confidently to a meeting are retained as unresolved, not assigned speculative titles.

**Dates.** Friday Project Showcase labelled 3 October in an original filename was actually held **2 October**. Academy recorded on **20 October** now has a video title corrected to that date. All model and regulatory observations should be read as contemporaneous October discussion, not live status.

**Rights and sensitive context.** Community disagreements are summarised without unnecessary names or unsupported allegations. The archive does not imply that participant-reported benchmarks, crypto protocols, medical claims or copyright interpretations have been independently validated.

## 12. Public recording and chapter index

This is a navigation register; the topic chapters above select only timestamps that add value. An edited excerpt and its parent meeting are linked together where the relation was supplied.

### A. Full meeting documents

#### Academy — 6 Oct

[Recording 1](https://www.youtube.com/watch?v=kC3p2LCUPlg)  
**Source:** `Academy 2026 10 06 Keri Evaluating and Benchmarking(1).docx`. **Chapters supplied:** 24.

- [00:00](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=0s) Introduction & Transparency Notice
- [01:33](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=93s) Technical Setup & Session Overview
- [03:00](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=180s) Trusting Agents & Defining "Correct" Behavior
- [04:12](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=252s) Walking Through the Jupyter Notebook & Test Setup
- [06:15](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=375s) The Heist Story Example & Failure Modes (Information Leakage)
- [10:10](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=610s) Group Discussion: Identifying How Agents Break
- [13:30](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=810s) Building Deterministic Rule-Based Safeguards
- [16:10](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=970s) Interpreting Positive Signals, Negative Signals & Null Values
- [21:15](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=1275s) Creating Evaluation Rubrics & Golden Datasets
- [23:00](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=1380s) Evaluating Abstract Outputs & Task Generalization
- [26:40](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=1600s) Using "LLM-as-Judge" & Model Independence
- [31:30](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=1890s) Quantifying Performance & Tracking Model Drift
- [33:50](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=2030s) Benchmarking the Judge & Variance in Scoring
- [36:45](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=2205s) Statistical Intuition: Overlap & Significant Differences
- [39:50](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=2390s) Q&A: Automating Evaluations & Logging Agent Traces
- [42:30](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=2550s) Regression Testing & Custom Model Benchmarks
- [45:45](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=2745s) Test-Driven Development (TDD) vs. "Vibe Coding"
- [48:40](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=2920s) Live Failure Mode: Token Limits & Context Exhaustion
- [52:15](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=3135s) Core Takeaways: How to Build Reliable Benchmarks
- [54:05](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=3245s) The Importance of Holdout Data Sets
- [57:00](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=3420s) Discussion: Frontloading Human Thinking in AI Workflows
- [01:01:40](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=3700s) Q&A: Interpreting Graphs & Trend Lines
- [01:08:50](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=4130s) Inferring Root Causes & Statistical Causation
- [01:14:50](https://www.youtube.com/watch?v=kC3p2LCUPlg&t=4490s) Wrap-Up, Future Topics & Final Thoughts

#### AI Stack — 7 Oct

[Recording 1](https://www.youtube.com/watch?v=tXeMMNCBN6s)  
**Source:** `AI Stack 2026 10 07(1).docx`. **Chapters supplied:** 13.

- [00:00](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=0s) Call kickoff and waiting for attendees
- [03:50](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=230s) Meeting intro: Purpose of local AI stacks and hardware sovereignty
- [10:16](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=616s) Member intro: Isaac (Biochemistry, protein modeling, and data science)
- [13:40](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=820s) Member intro: Jonathan (Alternative medicine database and hardware plans)
- [22:35](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=1355s) Member intro: Giulio (Broadcast engineering and home lab configurations)
- [43:00](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=2580s) Hardware discussion: Memory bandwidth and Mac Mini viability
- [45:10](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=2710s) Industry landscape: Regulations and regional AI constraints
- [01:00:50](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=3650s) Presentation: Agentic open-source harnesses (Pi v1.0, OpenCode, DeepSeek Harness)
- [01:11:00](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=4260s) Subscriptions & model pricing (OpenAI tiers, Anthropic, Google Gemini)
- [01:13:20](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=4400s) Open-weight options & credit plans (GLM, Kimi, MiniMax, Xiaomi MiMo)
- [01:33:05](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=5585s) Deep dive: Strata inference engine and MoE architecture
- [01:48:26](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=6506s) Strata benchmark analysis across consumer GPUs
- [02:09:10](https://www.youtube.com/watch?v=tXeMMNCBN6s&t=7750s) Q&A wrap-up and closing remarks

#### AI Stack — 14 Oct

[Recording 1](https://www.youtube.com/watch?v=laXj9v-Fs2o) · [Recording 2](https://www.youtube.com/watch?v=Qi-m_yfanCs)  
**Source:** `AI Stack 2026 10 14(1).docx`. **Chapters supplied:** 15.

The uploaded document supplies one chapter list for two parts, but does not identify the part-specific timeline. **Chapter-to-video alignment remains unverified**, so timestamps are listed without direct deep links.

`00:00` Introduction & Local AI vs. Cloud Costs; `01:46` Member Introductions & Used GPU Availability in Europe; `05:15` Manolo's Artificial Acceleration Platform & Hardware Price Tracking; `08:16` Data Center Hardware, Interconnects & Tensor Parallelism; `14:17` Model Release Acceleration & Intelligence Trends; `17:00` GPU Efficiency & Multi-GPU Setups (RTX vs. Workstation); `22:15` Paul’s Intro: Consulting & DGX Spark Experience; `26:05` Sean's Healthcare Startup & Transitioning from Cloud Grants to Local Models; `32:00` Local Hardware Realities: Speed vs. Usability; `34:44` Fine-Tuning Specialized Models & Data Privacy (HIPAA); `44:00` Ian’s Audio/Agency Journey & Philosophical Approach to AI; `52:16` Novice Guidance: Harnesses, Personal Setup & Where to Begin; `58:25` Hardware Check: RAM, GPU & Cloud/Subscription Alternatives; `01:05:20` Layered Data Security & Privacy Architectures; `01:12:00` Strata, Mini PCs & Hardware Purchasing Decision

#### AI Stack — 21 Oct

[Recording 1](https://www.youtube.com/watch?v=5_y9nyD72c0)  
**Source:** `AI Stack 2026 10 21(2).docx`. **Chapters supplied:** 18.

- [00:00](https://www.youtube.com/watch?v=5_y9nyD72c0&t=0s) Welcome, Introductions & Purpose of AI Stack Meeting
- [03:14](https://www.youtube.com/watch?v=5_y9nyD72c0&t=194s) Local AI vs. Cloud Subscriptions (Cost vs. Privacy)
- [09:25](https://www.youtube.com/watch?v=5_y9nyD72c0&t=565s) Community Q&A: Google Harness 2 & TensorFold Discussions
- [20:45](https://www.youtube.com/watch?v=5_y9nyD72c0&t=1245s) Best Budget GPUs for Running Qwen 27B (RX 6800 vs. RTX 3060 / 3090)
- [26:35](https://www.youtube.com/watch?v=5_y9nyD72c0&t=1595s) VRAM Requirements, Quantization (IQ3) & Inference Speed (Llama.cpp)
- [33:40](https://www.youtube.com/watch?v=5_y9nyD72c0&t=2020s) AI News Digest: Strata 0.2 Updates, Architecture & Upstream Forks
- [44:25](https://www.youtube.com/watch?v=5_y9nyD72c0&t=2665s) Strata Hardware Benchmarks (RTX 3060, Intel Arc A750, RX 6000 Series)
- [52:40](https://www.youtube.com/watch?v=5_y9nyD72c0&t=3160s) Beam 1.0 (Reflection AI): Benchmarks, Token Efficiency & Hallucinations
- [01:08:50](https://www.youtube.com/watch?v=5_y9nyD72c0&t=4130s) Free Models on OpenCode / KiloCode (GLM 5.3 Flash & MiniMax M3.1 Flash)
- [01:09:50](https://www.youtube.com/watch?v=5_y9nyD72c0&t=4190s) Audio & TTS Models: Yu2 Studio (Music Gen) & Drama 3 (TTS)
- [01:20:00](https://www.youtube.com/watch?v=5_y9nyD72c0&t=4800s) NVIDIA Nemotron 3.5 Super VL & Bolt
- [01:23:20](https://www.youtube.com/watch?v=5_y9nyD72c0&t=5000s) Fact-Checking China’s AI Export Control Measures
- [01:31:00](https://www.youtube.com/watch?v=5_y9nyD72c0&t=5460s) GPU Market Trends: RTX 5090 / 5080 Pricing & AMD Strix Halo
- [01:33:35](https://www.youtube.com/watch?v=5_y9nyD72c0&t=5615s) Fast Models & Infrastructure: Mercury 3, DeepInfer & Cloud TPUs
- [01:41:15](https://www.youtube.com/watch?v=5_y9nyD72c0&t=6075s) Hands-on Impressions: MiniMax M3.1 Flash & Local Quantization Limits
- [01:52:45](https://www.youtube.com/watch?v=5_y9nyD72c0&t=6765s) Advanced Harness Design: Intent-Aware Middleware & Deterministic Thinking
- [02:00:55](https://www.youtube.com/watch?v=5_y9nyD72c0&t=7255s) Local RAG & Embedding Models (Embedding Gemma 2)
- [02:02:45](https://www.youtube.com/watch?v=5_y9nyD72c0&t=7365s) Wrap-up & Next Steps

#### AI Stack — 28 Oct

[Recording 1](https://www.youtube.com/watch?v=lfFMutGNdi0)  
**Source:** `AI Stack 2026 10 28(1).docx`. **Chapters supplied:** 26.

- [00:00:00](https://www.youtube.com/watch?v=lfFMutGNdi0&t=0s) Introduction & Overview of the AI Stack Meeting
- [00:01:45](https://www.youtube.com/watch?v=lfFMutGNdi0&t=105s) Building Custom Agent Harnesses (Bun / Hot Dog Harness)
- [00:05:08](https://www.youtube.com/watch?v=lfFMutGNdi0&t=308s) Community Hardware Setups: AMD R9 9700, 128GB RAM & Qwen Coder
- [00:10:04](https://www.youtube.com/watch?v=lfFMutGNdi0&t=604s) Using AI Agents to Configure Systems & Set Up Strata
- [00:14:15](https://www.youtube.com/watch?v=lfFMutGNdi0&t=855s) Discussion on Model Fine-Tunes (Ornith vs. Base Models)
- [00:17:47](https://www.youtube.com/watch?v=lfFMutGNdi0&t=1067s) DeepSeek V4 Flash, Unified Memory & Inference Engines
- [00:20:08](https://www.youtube.com/watch?v=lfFMutGNdi0&t=1208s) Benchmarking Flint vs. Qwen 27B / 35B
- [00:27:25](https://www.youtube.com/watch?v=lfFMutGNdi0&t=1645s) GPU Market Dynamics: Used RTX 3080/3090 Prices & Crypto/AI Demand
- [00:35:15](https://www.youtube.com/watch?v=lfFMutGNdi0&t=2115s) Mac Apple Silicon Setups (M4 Max / M5 Pro), MLX & OMLX
- [00:40:10](https://www.youtube.com/watch?v=lfFMutGNdi0&t=2410s) Agent Harness Comparisons: Hermes, Pi, and DeepSeek Harnesses
- [00:48:15](https://www.youtube.com/watch?v=lfFMutGNdi0&t=2895s) Operating Systems for Local AI: Linux vs. Windows Configurations
- [00:52:05](https://www.youtube.com/watch?v=lfFMutGNdi0&t=3125s) Local AI Video & Image Generation Discussion
- [00:55:15](https://www.youtube.com/watch?v=lfFMutGNdi0&t=3315s) Weekly Presentation Begins: Strata 2.3–2.7 Performance Gains & Router Details
- [01:05:40](https://www.youtube.com/watch?v=lfFMutGNdi0&t=3940s) Strata Forks (Extended Strata, ARC Intel, Tesla V100, Multi-GPU)
- [01:09:37](https://www.youtube.com/watch?v=lfFMutGNdi0&t=4177s) Desa: Speech-to-Speech Model Without Text-in-the-Loop
- [01:12:17](https://www.youtube.com/watch?v=lfFMutGNdi0&t=4337s) Alibaba Apsara Amsterdam & Qwen 4 Speculation
- [01:15:10](https://www.youtube.com/watch?v=lfFMutGNdi0&t=4510s) Open Weights Deep Dive: Kimi K3.1 Pro & MiniMax M3.1 Flash
- [01:21:15](https://www.youtube.com/watch?v=lfFMutGNdi0&t=4875s) Flint 40B MoE Architecture & Benchmarks
- [01:29:36](https://www.youtube.com/watch?v=lfFMutGNdi0&t=5376s) Open Moss: JSON Layout-Controlled Image Generation
- [01:42:07](https://www.youtube.com/watch?v=lfFMutGNdi0&t=6127s) Mem0 / HiMemory 2.0 Agent State Persistence
- [01:44:54](https://www.youtube.com/watch?v=lfFMutGNdi0&t=6294s) Neotron 3.5 Transcribe & Llama.cpp 0.8
- [01:48:33](https://www.youtube.com/watch?v=lfFMutGNdi0&t=6513s) TensorFold & Google's Harness Squared Paper Discussion
- [01:57:48](https://www.youtube.com/watch?v=lfFMutGNdi0&t=7068s) Uncapping GeForce Tensor Cores (Linux Pre-Driver Module & Teraflop Gains)
- [02:03:48](https://www.youtube.com/watch?v=lfFMutGNdi0&t=7428s) Console Hardware Repurposing: PS5 Linux Exploit & BC250 APU
- [02:06:40](https://www.youtube.com/watch?v=lfFMutGNdi0&t=7600s) AI Policy & Compliance: EU AI Act, US GSA, and China CAC Regimes
- [02:10:08](https://www.youtube.com/watch?v=lfFMutGNdi0&t=7808s) Frontier vs. Open Models Gap, Cost Per Task & Wrap-Up

#### Augmented Minds — 1 Oct

[Recording 1](https://www.youtube.com/watch?v=ffHwyV0K0Ik)  
**Source:** `Augmented Minds 2026 10 01(2).docx`. **Chapters supplied:** 21.

- [00:00](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=0s) Intro, Housekeeping & Maryland Data Center News
- [00:53](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=53s) Augmented Mind Event Intro: The Human Side of AI
- [02:03](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=123s) The "New Normal" & Where Human Uniqueness Comes From
- [05:40](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=340s) The Dissolving Career "Talent Tree" & Navigating Uncertainty
- [09:48](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=588s) Community Thoughts: Fear of the Unknown & Generalist Buckets
- [12:18](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=738s) The AI Literacy Gap & Leveraging Domain Knowledge
- [18:15](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=1095s) Architects vs. Engineers: Human Taste, Experience & Direction
- [25:02](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=1502s) Human Taste, Aesthetic Judgment & AI Imitation Limits
- [27:50](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=1670s) Conscious Creators, Systems Thinking & Local AI
- [32:00](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=1920s) Balancing Vision and Execution: AI as an Augmentation Tool
- [39:20](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=2360s) Multidisciplinary Society, Employment & Helping for a Living
- [45:30](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=2730s) Overcoming Cognitive Hang-ups & What True Augmentation Means
- [53:15](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=3195s) The Shift from Pure Coding to Building Real Products
- [59:00](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=3540s) Task Deconstruction in the Workforce & Sustainable Business Models
- [01:04:00](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=3840s) Mindset, Overcoming Insecurities & Self-Care
- [01:08:35](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=4115s) Leading with Curiosity Rather than Competition
- [01:12:00](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=4320s) The Future of Mastery: What Can Only Human + AI Achieve?
- [01:18:25](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=4705s) Collective Intelligence: Augmenting Communities
- [01:23:50](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=5030s) High-Data Frontiers, "Human in the Loop" & Security at Scale
- [01:30:00](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=5400s) Common Sense, Environmental Context & Accessibility
- [01:40:30](https://www.youtube.com/watch?v=ffHwyV0K0Ik&t=6030s) Wrap-up & Upcoming Community Presentations Announcement

#### Augmented Minds — 8 Oct

[Recording 1](https://www.youtube.com/watch?v=Ro_8oRycSkE)  
**Source:** `Augmented Minds 2026 10 08(1).docx`. **Chapters supplied:** 22.

- [00:00](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=0s) Intro & Setup
- [01:05](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=65s) Vlad’s Exercise: Word Cloud on Problem Solving & AI
- [05:15](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=315s) Group Reflection on Shared Words (Observation, Empathy, Critical Thinking)
- [07:45](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=465s) Connecting Logical vs. Emotional Thinking
- [09:37](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=577s) Teaching Emotional Awareness to Machines
- [13:00](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=780s) Problem Rationale & Understanding the Field
- [15:38](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=938s) Types of Problems: Theoretical vs. Practical Experience
- [18:35](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=1115s) Deterministic vs. Open-Ended Problem Solving
- [21:05](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=1265s) Defining Ideal End States & Human Subjectivity
- [26:48](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=1608s) Initial Reactions to Early LLMs & Societal Impact
- [29:08](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=1748s) Challenging vs. Accepting AI Outputs
- [32:45](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=1965s) Rules, Frameworks, and Morality in Problem Solving
- [38:25](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=2305s) Local vs. Global Problem Solving & Setting Boundaries
- [42:00](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=2520s) AI as a Personal Mirror vs. World Models
- [43:30](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=2610s) Prompt Design: Encouraging Discomfort and Human Curiosity
- [48:25](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=2905s) Decomposing Large Problems into Agreeable Substrates
- [50:00](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=3000s) Game Theory, Empathy, and Coordination
- [54:20](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=3260s) Prompting Behavior: Conversational Loops & System States
- [58:25](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=3505s) Evolutionary Jumps & What AI Needs to Evolve
- [01:05:00](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=3900s) Probability Machines, Higher Dimensions & Intuition
- [01:14:15](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=4455s) Biological Triggers vs. Digital Analogues
- [01:18:15](https://www.youtube.com/watch?v=Ro_8oRycSkE&t=4695s) AI Ethics, Agency, and Wrap-Up

#### Coding Academy — 4 Oct

[Recording 1](https://www.youtube.com/watch?v=VlGwFvMAOUM)  
**Source:** `Coding Academy 2026 10 04(2).docx`. **Chapters supplied:** 17.

- [00:00](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=0s) Introduction & cross-lingual vector space convergence
- [01:26](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=86s) Language structure, grammar rules, and token efficiency
- [03:12](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=192s) Kantian philosophy: Sensorial perception vs. universal concepts
- [05:28](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=328s) Deterministic code vs. metaphysical layers & ontologies
- [08:16](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=496s) Mental models, perception, and how brains process reality
- [13:53](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=833s) Mapping ontological relationships, taxonomies, and primitives
- [20:00](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=1200s) Biological senses, electrical signaling, and neural architecture
- [23:45](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=1425s) Comparing LLMs to biological brains vs. hardware harnesses
- [31:00](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=1860s) Evolution, origins of complexity, and intentional system design
- [39:50](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=2390s) System 1 vs. System 2 thinking in cognitive models
- [43:30](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=2610s) Defining intelligence through game theory & problem-solving
- [47:30](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=2850s) Infinite regression vs. collective memory and resonance
- [55:30](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=3330s) Mathematical models: Euclidean geometry to quantum mechanics
- [58:15](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=3495s) Integrating memory directly into models vs. external vector stores
- [01:10:35](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=4235s) Language as lossy encoding for reality
- [01:14:45](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=4485s) Developing ontology primitives for agent orchestration
- [01:25:00](https://www.youtube.com/watch?v=VlGwFvMAOUM&t=5100s) Hardware acceleration, LLM-on-chip ASICs & speculative decoding

#### Creative AI Video Lab — 12 Oct

[Recording 1](https://www.youtube.com/watch?v=A7sIYEGmMI8)  
**Source:** `Creative AI Video Lab 2026 10 12(1).docx`. **Chapters supplied:** 18.

- [00:00](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=0s) Introduction: Discovering the viral "slopcore" trend and how it exploded online.
- [01:25](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=85s) Dissecting a Viral Slopcore Video: Full AI pipeline, meme lore, and visual styling.
- [02:44](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=164s) The Creator’s Process & Open-Source Pipeline: Analyzing the $600 PDF breakdown, character reuse, and automation.
- [04:46](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=286s) Technical Anatomy: Midjourney assets, Seedance animations, and JavaScript/CSS video effects.
- [05:40](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=340s) Generating the Audio in Suno: Crafting a sci-fi song concept and lore for the track.
- [07:23](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=443s) Planning the Visual Pipeline: Static frames vs. animated video clips and keeping costs controlled.
- [10:16](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=616s) Automated vs. "Babysitting": Why autonomous generation often needs human direction and taste.
- [13:00](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=780s) Designing the Main Character: Crafting the sci-fi android protagonist.
- [14:06](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=846s) Community Discussion & Platform Reach: Audience response across platforms.
- [16:15](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=975s) Cost Management: Breaking down API expenses, failed generations, and asset budgeting.
- [18:28](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=1108s) Q&A / Discussion: Scripting UI interactions, Claude Code workflows, and automating browser scenes.
- [24:45](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=1485s) Directing the Intro Scene: Step-by-step assembly of spaceship visuals, timing cuts, and beat detection.
- [30:20](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=1820s) Creative Hacks: Using crops, 2.5D rotations, and small local models to stretch image assets.
- [33:02](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=1982s) Discussion on Generation Costs: Chat subscriptions vs. API usage and local hardware limitations.
- [38:25](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=2305s) Lip Sync & Character Performance: Using Seedance 2.5, speech timing adjustments, and JS overlays.
- [43:26](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=2606s) Iteration & Asset Scraping: Fine-tuning gestures, discarded images, and refining the narrative arc.
- [47:20](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=2840s) YouTube Performance Breakdown: Search traffic, audience interest signals, and reach.
- [52:27](https://www.youtube.com/watch?v=A7sIYEGmMI8&t=3147s) Cross-Platform Comparison & Wrap-up: Final reflections and closing thoughts.

#### Creative AI Video Lab — 19 Oct

[Recording 1](https://www.youtube.com/watch?v=3hMbjGMkv4s)  
**Source:** `Creative AI Video Lab  2026 10 19.docx`. **Chapters supplied:** 15.

- [00:00](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=0s) Introduction: Hyperframes and AI Movie-Making Repositories
- [03:04](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=184s) Use Case: Automating Youth Sports Highlights from 4K Raw Footage
- [06:17](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=377s) Generic Video Pipelines: Building Custom Editing Workflows with FFmpeg
- [08:44](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=524s) Demo: Claude Code Terminal Recording, AI Text Overlays & Graphic Inserts
- [11:06](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=666s) Multi-Model Video Generation (Sci-Fi Animation & Lip-Sync Demos)
- [13:15](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=795s) Visual Annotators vs. Command-Line Agents & Render Cycles
- [16:24](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=984s) Open Source vs. Proprietary Tools (DaVinci Resolve & Hyperframes Discussion)
- [19:07](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=1147s) On-Screen Visual Annotation & Guiding AI Video Prompts
- [22:26](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=1346s) Forking Open-Source Repositories with AI Agents
- [24:02](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=1442s) MiniMax Licensing, Watermarking, and Copyright Protections
- [27:20](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=1640s) AI Safety Guardrails, Commercial Use, and Human Authorship Laws
- [29:00](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=1740s) Music Copyright, Sampling Precedents, and Creator vs. User Rights
- [32:24](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=1944s) Suno Music Generation: Human Input, Note Patterns, and Infringement Lawsuits
- [40:26](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=2426s) Platform Policies: Duplicated AI Content & Channel Moderation
- [46:16](https://www.youtube.com/watch?v=3hMbjGMkv4s&t=2776s) Voice Cloning Controversies, ElevenLabs, and Protecting Audio Identity

#### Creative AI Video Lab — 26 Oct

[Recording 1](https://www.youtube.com/watch?v=V6INncVVdco)  
**Source:** `Creative AI Video Lab 2026 10 26.docx`. **Chapters supplied:** 13.

- [00:00](https://www.youtube.com/watch?v=V6INncVVdco&t=0s) UI tools & bounding box prompt workflows
- [01:28](https://www.youtube.com/watch?v=V6INncVVdco&t=88s) Testing corridor chase scene generation (Omni model results & style drift)
- [04:42](https://www.youtube.com/watch?v=V6INncVVdco&t=282s) Comparing results with Kling and SeaDance; issues with start/end frames
- [08:15](https://www.youtube.com/watch?v=V6INncVVdco&t=495s) Discussion on context drift, multi-image references, and starting motions
- [12:56](https://www.youtube.com/watch?v=V6INncVVdco&t=776s) Strategy: Overgenerating footage and rough cutting best clips
- [14:18](https://www.youtube.com/watch?v=V6INncVVdco&t=858s) Testing camera blocking schemes vs. visual storyboards for fight scenes
- [21:35](https://www.youtube.com/watch?v=V6INncVVdco&t=1295s) SeaDance storyboard test results, cleaning up arrow artifacts, and lessons learned
- [24:05](https://www.youtube.com/watch?v=V6INncVVdco&t=1445s) Reflections on commercial AI video tools vs. custom workflows
- [27:46](https://www.youtube.com/watch?v=V6INncVVdco&t=1666s) Evaluating local video models (MiniMax, LTX) & hardware comparisons (Mac vs. RTX)
- [32:00](https://www.youtube.com/watch?v=V6INncVVdco&t=1920s) Channel performance check-in, traffic trends, and online hype
- [34:40](https://www.youtube.com/watch?v=V6INncVVdco&t=2080s) Reviewing external AI creator workflows, aesthetics, and sponsorship models
- [38:30](https://www.youtube.com/watch?v=V6INncVVdco&t=2310s) Cost barrier of cutting-edge video models and creative philosophy around remix culture
- [46:30](https://www.youtube.com/watch?v=V6INncVVdco&t=2790s) Parallels to music sampling/white label culture & wrap-up

#### Friday Project Showcase — 2 Oct

[Recording 1](https://www.youtube.com/watch?v=pN1OKmuPR_E)  
**Source:** `Friday Project Showcase 2026 10 03(1).docx`. **Chapters supplied:** 20.

- [00:00](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=0s) Welcome & Introductions
- [01:23](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=83s) Sven: AI Basics & System Architecture
- [04:21](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=261s) Sven: How LLMs & Transformers Work
- [05:36](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=336s) Sven: Human-AI Workflow & Software Stacks
- [07:20](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=440s) Sven: Local vs. Cloud Hardware & Security
- [09:50](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=590s) Sven: Processing Hardware (CPU, Unified Memory, GPU)
- [11:13](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=673s) Sven: Model Parameter Sizes & Scaling
- [13:02](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=782s) Sven: Tokens, Hardware Costs & MoE vs. Dense Models
- [15:56](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=956s) Sven: Quantization & Context Window Management
- [19:07](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=1147s) Sven: Real-World Use Cases & Engineering Simulations
- [24:16](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=1456s) Q&A: Community Discussion & Feedback on Sven's Talk
- [32:35](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=1955s) Dustin: Introduction & Background
- [37:30](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=2250s) Dustin: Demo – 3D Facility Modeler & Flight Simulator
- [41:04](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=2464s) Dustin: Simulation Engine & SOP Workflow Automation
- [44:06](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=2646s) Dustin: Rapid Website Rebuild & Bid Estimator Tool
- [48:04](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=2884s) Dustin: Warehouse "Untangler" & Facility Simulations
- [55:05](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=3305s) Q&A & Discussion: Architectural Design, Construction & Open-Source
- [1:09:48](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=4188s) Dustin: Hardware, Model Stack & Development Costs
- [1:27:07](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=5227s) Dustin: Open Source Strategy & Building Publicly
- [1:28:55](https://www.youtube.com/watch?v=pN1OKmuPR_E&t=5335s) Wrap-Up & Next Steps

#### Friday Project Showcase — 9 Oct

[Recording 1](https://www.youtube.com/watch?v=BWcljSnAwgw)  
**Source:** `Friday Project Showcase 2026 10 09(1).docx`. **Chapters supplied:** 12.

- [00:00](https://www.youtube.com/watch?v=BWcljSnAwgw&t=0s) Welcome & Open Floor Kickoff
- [05:40](https://www.youtube.com/watch?v=BWcljSnAwgw&t=340s) Tone, "Abuse" Policies & Output Degradation
- [13:00](https://www.youtube.com/watch?v=BWcljSnAwgw&t=780s) Prompt Optimization: Pre-processing Layers vs. Raw Dictation
- [22:40](https://www.youtube.com/watch?v=BWcljSnAwgw&t=1360s) Iterative Prompt Engineering & Multi-Agent Context Handling
- [27:50](https://www.youtube.com/watch?v=BWcljSnAwgw&t=1670s) Autonomous Agents: Cognitive Loops & Memory Chronicles
- [38:35](https://www.youtube.com/watch?v=BWcljSnAwgw&t=2315s) Human-AI Interaction & Voice/TTS Implementations
- [43:40](https://www.youtube.com/watch?v=BWcljSnAwgw&t=2620s) Harness Breakdown: Hermes vs. OpenClaw vs. Pi Agent
- [01:06:05](https://www.youtube.com/watch?v=BWcljSnAwgw&t=3965s) Local Multi-Agent Orchestrators & Telemetry Considerations
- [01:09:40](https://www.youtube.com/watch?v=BWcljSnAwgw&t=4180s) Showcase: Ethan’s Multi-Agent Sandbox & Dream RSI Architecture
- [01:23:25](https://www.youtube.com/watch?v=BWcljSnAwgw&t=5005s) AI Security, Privacy Risks & Local Hardware Auditing
- [01:39:45](https://www.youtube.com/watch?v=BWcljSnAwgw&t=5985s) Local Benchmarking & Hardware Concurrency (Mac Studio vs. RTX 5090)
- [01:43:00](https://www.youtube.com/watch?v=BWcljSnAwgw&t=6180s) Data Sovereignty & Closing Thoughts

#### Project Showcase — 16 Oct

[Recording 1](https://www.youtube.com/watch?v=sLQLyts4Vko)  
**Source:** `Project Showcase 2026 10 16.docx`. **Chapters supplied:** 25.

- [00:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=0s) Welcome, recording disclaimer, and showcase intro
- [04:08](https://www.youtube.com/watch?v=sLQLyts4Vko&t=248s) Valentino: Iron Jarvis updates & new local-only mode
- [05:35](https://www.youtube.com/watch?v=sLQLyts4Vko&t=335s) Interactive visual UI outputs & multi-model routing
- [07:33](https://www.youtube.com/watch?v=sLQLyts4Vko&t=453s) Terminal build pane & QuickBooks AI alternative (Iron Books)
- [09:18](https://www.youtube.com/watch?v=sLQLyts4Vko&t=558s) Case study: Using Valentino's MCP repo for tax workflows
- [12:35](https://www.youtube.com/watch?v=sLQLyts4Vko&t=755s) Status dashboard, pop-out multi-screen windows & durable agents
- [13:30](https://www.youtube.com/watch?v=sLQLyts4Vko&t=810s) Local browser agent extension demo
- [14:42](https://www.youtube.com/watch?v=sLQLyts4Vko&t=882s) Overview of GitHub repositories & AI learning quest prompts
- [19:14](https://www.youtube.com/watch?v=sLQLyts4Vko&t=1154s) Discussion: Will AI replace CPAs, paralegals, and knowledge workers?
- [24:55](https://www.youtube.com/watch?v=sLQLyts4Vko&t=1495s) Accessibility feedback: Designing UI toggles for color blindness
- [28:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=1680s) Handling context drift and multi-agent task orchestration
- [30:53](https://www.youtube.com/watch?v=sLQLyts4Vko&t=1853s) Exploring Inkbox (giving AI agents phone numbers & outbound calling)
- [33:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=1980s) Intermission & transition to the next presenter
- [35:45](https://www.youtube.com/watch?v=sLQLyts4Vko&t=2145s) Vlad: Intro to Cyber Alchemy Lab & AI Governance Architecture
- [37:37](https://www.youtube.com/watch?v=sLQLyts4Vko&t=2257s) The Three Core Lenses: Authority, Provenance, and Life Cycles
- [41:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=2460s) Applied Example: Marketing campaign AB testing & defining "qualified leads"
- [48:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=2880s) Evolving criteria and tracking definition versions (V1 vs. V2)
- [52:14](https://www.youtube.com/watch?v=sLQLyts4Vko&t=3134s) Crafting a software factory & architectural code enforcement
- [55:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=3300s) Documentation walkthrough & defining axioms, boundaries, and terms
- [1:00:30](https://www.youtube.com/watch?v=sLQLyts4Vko&t=3630s) Preventing model hallucination through rigid definition boundaries
- [1:07:20](https://www.youtube.com/watch?v=sLQLyts4Vko&t=4040s) Balancing cognitive complexity and user implementation
- [1:13:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=4380s) Unifying scattered company knowledge into an integrated "brain"
- [1:15:00](https://www.youtube.com/watch?v=sLQLyts4Vko&t=4500s) Maintaining human tone vs. generic LLM outputs
- [1:18:33](https://www.youtube.com/watch?v=sLQLyts4Vko&t=4713s) Context windows, ephemerality, and MCP tooling for agent systems
- [1:20:40](https://www.youtube.com/watch?v=sLQLyts4Vko&t=4840s) Community shout-outs, local hardware journeys, and wrap-up

#### Friday Project Showcase — 30 Oct

[Recording 1](https://www.youtube.com/watch?v=tTa1sAl3k_o)  
**Source:** `Friday Project Showcase 2026 10 31.docx`. **Chapters supplied:** 25.

- [00:00:00](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=0s) Intro and setup by Mel
- [00:03:50](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=230s) Adriano’s presentation begins: AI through the library system
- [00:06:55](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=415s) Historical deep dives vs. modern tech books (1960s systems vs. today)
- [00:09:02](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=542s) Starting inspiration: Drowning in options without sequence
- [00:11:37](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=697s) Adriano’s background in media, communications, and critical theory
- [00:17:38](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=1058s) Framing AI beyond doom/gloom: Force, friction, work, and leisure
- [00:24:17](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=1457s) The library study: Exploring 25+ urban and rural libraries
- [00:26:20](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=1580s) Corporate silos in AI and Santander’s open-source approach
- [00:29:25](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=1765s) Physical research discoveries: Locational memory and tactile focus
- [00:33:45](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=2025s) Library navigation: Dewey Decimal (006) vs. Library of Congress (QA)
- [00:37:48](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=2268s) Contextual discoveries: Audience awareness and classification quirks
- [00:41:55](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=2515s) Human adaptability: The psychological immune system and tech shocks
- [00:44:30](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=2670s) Computing pioneers & the metaphysics of intuition in AI
- [00:47:12](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=2832s) Green fields: Regional library biases (rural 3D printing vs. urban finance)
- [00:52:03](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=3123s) Signal-to-noise ratio and missing modern topics (social media bans, youth devices)
- [00:58:34](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=3514s) Unconventional discoveries: Afrofuturism and W.E.B. Du Bois infographics
- [01:01:10](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=3670s) Richard Susskind, synthetic data, and AI "dreaming"
- [01:04:30](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=3870s) Concluding goals: Youth outreach and education
- [01:05:30](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=3930s) Q&A begins: Mel suggests standardizing a library research framework
- [01:09:22](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=4162s) Steve on intake frameworks and early memories of libraries
- [01:18:18](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=4698s) Trevor asks about the specific call to action for youth
- [01:24:05](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=5045s) Manolo on physical reality vs. algorithms and creative risk-taking
- [01:42:12](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=6132s) Steve on cultural incentives and attention allocation
- [01:50:58](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=6658s) Manolo on narrative design and audience resonance
- [01:59:12](https://www.youtube.com/watch?v=tTa1sAl3k_o&t=7152s) Mel on slide presentation strategy and focusing on one core idea

#### Academy — 20 Oct

[Recording 1](https://www.youtube.com/watch?v=Gnq1l3ZlDGA)  
**Source:** `ResonantDAO Academy 2026 10 20(1).docx`. **Chapters supplied:** 20.

- [00:00:00](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=0s) Welcome, check-in, and self-assessment of AI experience levels
- [00:02:55](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=175s) Frustrations & capabilities of working with agentic AI
- [00:04:45](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=285s) The nature of LLMs: Probabilistic engines and the "Actor" analogy
- [00:07:15](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=435s) Hallucinations, error rates, and model benchmarks
- [00:10:30](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=630s) Defining the stack: Model (engine) vs. Harness (car)
- [00:13:55](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=835s) Managing context windows and short-term vs. long-term memory
- [00:24:20](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=1460s) Deep dive: How models "reason" and why they display thinking tokens
- [00:31:05](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=1865s) Q&A: Optimizing languages, token efficiency, and layered memory
- [00:37:05](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=2225s) Context engineering: Mitigating noise and crafting precise prompts
- [00:47:15](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=2835s) Demo: Inspecting token usage & context windows in DeepSeek/Pi harness
- [00:53:20](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=3200s) Sandbox environments, security, and desktop browser agents
- [00:57:00](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=3420s) Demo: Augmentor Agent controlling the browser (Amazon deal search)
- [01:00:25](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=3625s) Q&A: AI voice/video artifacts
- [01:05:00](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=3900s) Tutorial start: Introduction to OpenCode Desktop
- [01:09:45](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=4185s) OpenCode desktop installation vs. CLI & setup requirements
- [01:15:30](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=4530s) Folder configuration, project settings, and account privacy
- [01:21:40](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=4900s) Overview of free models available in OpenCode (Beam, MiniMax, DeepSeek, Neatron)
- [01:28:30](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=5310s) Integrating web search & scraping (Firecrawl vs. Exa)
- [01:32:40](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=5560s) Live test: Javier builds an HTML project using OpenCode
- [01:39:30](https://www.youtube.com/watch?v=Gnq1l3ZlDGA&t=5970s) Community wrap-up, weekly schedule, and questions on Augmentor Agent / Resonant OS

#### ResonantDAO Exploration — 12 Oct

[Recording 1](https://www.youtube.com/watch?v=0PRtiGZS2KE)  
**Source:** `Resonant DAO Exploration and Community Sync 2026 10 12(1).docx`. **Chapters supplied:** 18.

- [00:00](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=0s) Welcome, Recording Disclaimer, & Introduction
- [02:30](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=150s) Resonant DAO Vision: Co-Ownership & The Contribution Economy
- [06:15](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=375s) Technical Architecture: Solana Deployment & The 22 Contribution Dimensions
- [08:10](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=490s) Workflow Demo: Tracking Contribution Lifecycles & Proofs
- [13:20](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=800s) Handling Durable Evidence & Decentralized Storage Needs
- [16:20](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=980s) Why Bottom-Up Ownership Matters in the Age of AI Disruption
- [19:00](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=1140s) Mapping Human & AI Actions Through Archetypal Story Reading
- [26:15](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=1575s) Resonant OS Development & Tooling Updates
- [27:40](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=1660s) Community Discussion & Capital Injection Plans
- [33:20](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=2000s) The Shift in SaaS & Creating Shared Community Infrastructure
- [37:40](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=2260s) Discord Growth & Community Scalability
- [43:00](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=2580s) Welcoming Winston: Background in Aerospace, Formal Verification, & Crypto
- [52:00](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=3120s) Software Rigor, Agile vs. Waterfall, & Foundations of AI Coding
- [01:03:00](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=3780s) The Need for Mathematical Modeling in Tokenomics
- [01:08:00](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=4080s) Retaining Human Knowledge & Organic Learning with AI
- [01:17:40](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=4660s) Token Design: Reputation Tokens, Speculative Pools, & Algorithmic Growth
- [01:21:20](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=4880s) Scaling Community Power Ahead of the Next Market Cycle
- [01:25:30](https://www.youtube.com/watch?v=0PRtiGZS2KE&t=5130s) Upcoming Community Calls, Presentations, & Wrap-Up

### B. Edited video extracts and supplementary recordings

#### ResonantOS Deep Dive — Modular Routing, Plugins & Sovereignty

**Date/context:** 2026-10-03. **Recording:** [mlwy2QS_n7o](https://www.youtube.com/watch?v=mlwy2QS_n7o). **Status:** Edited excerpt; exact session date/title based on earlier YouTube inventory. 

#### ResonantDAO: The Decentralised DAO — Contribution / Voting

**Date/context:** 2026-10-05. **Recording:** [tKLRhz5_4YM](https://www.youtube.com/watch?v=tKLRhz5_4YM). **Status:** Edited excerpt; description in original inventory. 

#### A Local Powerhouse: Dual Blackwell 6000s + RTX 5090

**Date/context:** October date not confirmed. **Recording:** [Cv6n_-yPLVg](https://www.youtube.com/watch?v=Cv6n_-yPLVg). **Status:** Edited Sunday Co-Op excerpt; community-reported setup. 

- [00:00](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=0s) Welcome & Introductions
- [00:24](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=24s) Dual Blackwell 6000s, RTX 5090 & Threadripper Pro
- [00:56](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=56s) Hermes and SEC/S&P 500 paper-trading pipeline
- [01:22](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=82s) Renting compute workspaces
- [02:42](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=162s) Front-end tooling and telemetry concerns
- [04:11](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=251s) Community schedule
- [06:32](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=392s) Enterprise local AI deployments
- [08:10](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=490s) Power and leasing Mac Studios
- [11:38](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=698s) Local + frontier model orchestration
- [13:03](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=783s) Model licensing
- [15:27](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=927s) Paperclip impressions
- [16:07](https://www.youtube.com/watch?v=Cv6n_-yPLVg&t=967s) Telemetry APIs, agent loops and 2FA

#### ResonantDAO Contribution Economy — short introduction

**Date/context:** 2026-10-12. **Recording:** [ar9FzY990q8](https://www.youtube.com/watch?v=ar9FzY990q8). **Status:** Edited from full DAO Exploration 12 October meeting. **Parent session:** [full recording](https://www.youtube.com/watch?v=0PRtiGZS2KE).

- [00:00](https://www.youtube.com/watch?v=ar9FzY990q8&t=0s) Intro & AI Artisans
- [01:04](https://www.youtube.com/watch?v=ar9FzY990q8&t=64s) The Contribution Economy
- [02:08](https://www.youtube.com/watch?v=ar9FzY990q8&t=128s) Solana architecture roadmap
- [02:47](https://www.youtube.com/watch?v=ar9FzY990q8&t=167s) The 22 archetypes
- [04:56](https://www.youtube.com/watch?v=ar9FzY990q8&t=296s) Bottom-up governance
- [07:03](https://www.youtube.com/watch?v=ar9FzY990q8&t=423s) Story and value mapping
- [08:29](https://www.youtube.com/watch?v=ar9FzY990q8&t=509s) Automated logging
- [09:21](https://www.youtube.com/watch?v=ar9FzY990q8&t=561s) Resonant OS and SDK
- [10:01](https://www.youtube.com/watch?v=ar9FzY990q8&t=601s) Capital and scaling
- [11:32](https://www.youtube.com/watch?v=ar9FzY990q8&t=692s) AI disruption and future-proofing

#### AI Stack Models, Benchmarks and Cloning

**Date/context:** 2026-10-14. **Recording:** [Qi-m_yfanCs](https://www.youtube.com/watch?v=Qi-m_yfanCs). **Status:** Edited news segment from AI Stack 14 October. **Parent session:** [full recording](https://www.youtube.com/watch?v=laXj9v-Fs2o).

#### AI Models, Context and Memory — Manolo Remiddi

**Date/context:** 2026-10-20. **Recording:** [T-ia3p6BOI0](https://www.youtube.com/watch?v=T-ia3p6BOI0). **Status:** Edited Academy lesson. **Parent session:** [full recording](https://www.youtube.com/watch?v=Gnq1l3ZlDGA).

- [00:00](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=0s) Probabilistic engines
- [00:46](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=46s) Actor analogy and hallucinations
- [02:41](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=161s) Benchmarks and hallucinations
- [03:07](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=187s) Beginner vs intermediate users
- [04:22](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=262s) Harness versus model
- [06:13](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=373s) Open-source interfaces
- [07:56](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=476s) Context windows and working memory
- [10:19](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=619s) External memory and tools
- [11:19](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=679s) Missing information and hallucinations
- [12:18](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=738s) Local model reasoning demo
- [14:28](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=868s) Prompt vagueness and memory noise
- [16:40](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=1000s) Clarity versus token saving
- [18:00](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=1080s) Instructing retrieval first
- [19:23](https://www.youtube.com/watch?v=T-ia3p6BOI0&t=1163s) Summary

#### The Augmentor Harness: Local AI Agent Demo

**Date/context:** 2026-10-20. **Recording:** [p3KBOgxTd_E](https://www.youtube.com/watch?v=p3KBOgxTd_E). **Status:** Edited Academy demonstration. **Parent session:** [full recording](https://www.youtube.com/watch?v=Gnq1l3ZlDGA).

- [00:00](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=0s) Experimental UI and context viewer
- [01:15](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=75s) Token breakdown
- [02:20](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=140s) Tool efficiency
- [03:40](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=220s) DeepSeek integration
- [05:05](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=305s) Linux and sandboxing
- [06:18](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=378s) Browser agent demo
- [07:15](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=435s) Permission troubleshooting
- [08:30](https://www.youtube.com/watch?v=p3KBOgxTd_E&t=510s) Results and reflections

#### OpenCode Setup — Chris

**Date/context:** 2026-10-20. **Recording:** [BcRfRs3_XBI](https://www.youtube.com/watch?v=BcRfRs3_XBI). **Status:** Edited Academy tutorial. **Parent session:** [full recording](https://www.youtube.com/watch?v=Gnq1l3ZlDGA).

- [00:00](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=0s) OpenCode Desktop for Windows
- [00:46](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=46s) CLI/TUI versus Desktop
- [02:04](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=124s) Installation and config
- [02:55](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=175s) Account privacy
- [04:13](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=253s) Project-folder isolation
- [05:28](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=328s) Models
- [06:26](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=386s) Firecrawl and Exa
- [07:50](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=470s) Environment variables
- [08:33](https://www.youtube.com/watch?v=BcRfRs3_XBI&t=513s) Kilo Code and wrap-up

#### Strata v0.2, Beam 1.0 & RTX 5090 News — AI News Digest

**Date/context:** 2026-10-21. **Recording:** [mdDXjeAdr0Q](https://www.youtube.com/watch?v=mdDXjeAdr0Q). **Status:** Edited from AI Stack 21 October. **Parent session:** [full recording](https://www.youtube.com/watch?v=5_y9nyD72c0).

- [00:00](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=0s) Strata v0.2
- [00:33](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=33s) Security fixes and rollback
- [01:12](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=72s) PolyStrata forks
- [01:46](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=106s) macOS and Docker
- [02:03](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=123s) Qwen and performance
- [02:37](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=157s) Ultra-low quantisation
- [02:58](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=178s) NVFP4 and Mistral
- [03:20](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=200s) GPU benchmarks
- [04:21](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=261s) Intel Arc gains
- [05:14](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=314s) Beam 1.0
- [06:08](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=368s) Beam architecture
- [06:49](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=409s) API availability
- [07:30](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=450s) Drama 3
- [08:29](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=509s) Multi-speaker TTS
- [09:33](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=573s) GPU market rumours
- [10:41](https://www.youtube.com/watch?v=mdDXjeAdr0Q&t=641s) Local PII masking

#### ResonantDAO Updates

**Date/context:** 2026-10-26. **Recording:** [6quDsU24xEI](https://www.youtube.com/watch?v=6quDsU24xEI). **Status:** Edited community working session; described by user. 

- [00:00](https://www.youtube.com/watch?v=6quDsU24xEI&t=0s) UI redesign
- [02:03](https://www.youtube.com/watch?v=6quDsU24xEI&t=123s) Contribution economy
- [04:05](https://www.youtube.com/watch?v=6quDsU24xEI&t=245s) Workflow lifecycle
- [06:14](https://www.youtube.com/watch?v=6quDsU24xEI&t=374s) Bounties and tribes
- [08:18](https://www.youtube.com/watch?v=6quDsU24xEI&t=498s) Decentralised data storage
- [13:07](https://www.youtube.com/watch?v=6quDsU24xEI&t=787s) AI security and sovereignty
- [24:36](https://www.youtube.com/watch?v=6quDsU24xEI&t=1476s) Experimental CRABS permissions
- [36:18](https://www.youtube.com/watch?v=6quDsU24xEI&t=2178s) Experimental EOTH authentication
- [41:32](https://www.youtube.com/watch?v=6quDsU24xEI&t=2492s) Next steps

#### 120B MoE on 16GB VRAM + 2× Faster RTX Prefill — AI News Digest

**Date/context:** 2026-10-28. **Recording:** [bQ27yH0hggs](https://www.youtube.com/watch?v=bQ27yH0hggs). **Status:** Edited from AI Stack 28 October. **Parent session:** [full recording](https://www.youtube.com/watch?v=lfFMutGNdi0).

- [00:00](https://www.youtube.com/watch?v=bQ27yH0hggs&t=0s) Strata MoE VRAM optimisations
- [03:55](https://www.youtube.com/watch?v=bQ27yH0hggs&t=235s) Desa speech model
- [06:27](https://www.youtube.com/watch?v=bQ27yH0hggs&t=387s) Flint on Apple Silicon
- [08:47](https://www.youtube.com/watch?v=bQ27yH0hggs&t=527s) MOSS visual layout
- [11:26](https://www.youtube.com/watch?v=bQ27yH0hggs&t=686s) Tensorfold inference
- [13:58](https://www.youtube.com/watch?v=bQ27yH0hggs&t=838s) Harness Squared
- [16:17](https://www.youtube.com/watch?v=bQ27yH0hggs&t=977s) GeForce Tensor Core workaround

#### ResonantOS Academy AMA

**Date/context:** 2026-10-27. **Recording:** [iaIoTd38WdU](https://www.youtube.com/watch?v=iaIoTd38WdU). **Status:** Public video described by user; no matching meeting DOCX. 

- [00:00:00](https://www.youtube.com/watch?v=iaIoTd38WdU&t=0s) CUDA
- [00:00:42](https://www.youtube.com/watch?v=iaIoTd38WdU&t=42s) 24/7 compute and costs
- [00:03:00](https://www.youtube.com/watch?v=iaIoTd38WdU&t=180s) Apple M1 Max versus budget PC
- [00:04:30](https://www.youtube.com/watch?v=iaIoTd38WdU&t=270s) Strata and Linux
- [00:07:55](https://www.youtube.com/watch?v=iaIoTd38WdU&t=475s) Qwen 4 speculation
- [00:10:10](https://www.youtube.com/watch?v=iaIoTd38WdU&t=610s) Memory tiering
- [00:11:05](https://www.youtube.com/watch?v=iaIoTd38WdU&t=665s) Dual RTX 3060
- [00:13:15](https://www.youtube.com/watch?v=iaIoTd38WdU&t=795s) Qwen speculation
- [00:17:15](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1035s) Linux learning
- [00:18:00](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1080s) Update security
- [00:20:00](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1200s) DeepSeek agent harness
- [00:22:20](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1340s) Linux VM Chromebooks
- [00:24:30](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1470s) RTX 5090/NVMe
- [00:27:10](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1630s) Open source licensing
- [00:31:00](https://www.youtube.com/watch?v=iaIoTd38WdU&t=1860s) DAO values and IP
- [00:34:30](https://www.youtube.com/watch?v=iaIoTd38WdU&t=2070s) Screening guest projects

### C. Documentary-only and unresolved material

- **Friday Project Showcase 23 October, parts 1 and 2:** notes supplied; recordings marked private. No public video link is provided.
- **AI Stack News 21 October (inventory item #23):** private; excluded from the public index.
- **October 12 shortened DAO DOCX:** chapters correspond to the edited video `ar9FzY990q8`, not to the full meeting timeline.
- **Unmatched public video candidates from the previously supplied 31-link inventory:** `3plApJL8MLU`, `AgI1gjPHv8E` and potentially additional excerpts that do not have a user-confirmed source/title pairing in the current documents. Their titles, visibility or related sessions should not be guessed.
- **Oct 14 AI Stack part 2:** video URL is provided but the shared chapter list needs checking against the two recordings before assigning deep links.

## 13. Editorial maintenance

When updating later months, preserve the month and exact source date with every performance claim; use source-level direct links; distinguish current implementations from roadmaps; retain disagreements when useful; and prevent multiple edited clips of a single meeting from inflating the number of sessions represented.
