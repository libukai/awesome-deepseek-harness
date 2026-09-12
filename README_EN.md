<div>
  <p align="center">
    <img width="100%" alt="Agent = Model + Harness — a luminous whale connecting the DSH ecosystem" src="assets/media/awesome-deepseek-harness-banner.png">
  </p>
</div>

<p align="center">
  <a href="README.md">简体中文</a> · English · <a href="README_JA.md">日本語</a>
</p>

<p align="center">
  The ultimate guide to DeepSeek Harness: resources, tutorials, plugins, and tools<br>
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="https://github.com/topics/dsh-plugin"><img src="https://img.shields.io/badge/GitHub-dsh--plugin-0969da?style=flat-square" alt="GitHub topic: dsh-plugin"></a>
  <a href="https://github.com/libukai/awesome-deepseek-harness/stargazers"><img src="https://img.shields.io/github/stars/libukai/awesome-deepseek-harness?style=flat-square" alt="GitHub Stars"></a>
  <a href="https://github.com/libukai/awesome-deepseek-harness/issues"><img src="https://img.shields.io/badge/Issues-welcome-brightgreen.svg?style=flat-square" alt="Issues welcome"></a>
</p>

This project follows a curated, quality-over-quantity approach to collecting excellent DeepSeek Harness resources and building a richer Agent ecosystem with AI practitioners.

> If this project helps you, please consider giving it a ⭐. You can also follow [@李不凯正在研究](https://x.com/libukai) on X for more hands-on Agent content.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Quick Start](#quick-start)
  - [Launch the Web UI](#launch-the-web-ui)
  - [Run from Source](#run-from-source)
  - [Use the Python SDK](#use-the-python-sdk)
  - [Install Plugins](#install-plugins)
- [Official Resources](#official-resources)
  - [Packages and Integrations](#packages-and-integrations)
  - [Source Repositories](#source-repositories)
  - [Official Documentation](#official-documentation)
  - [Community](#community)
- [Community Resources](#community-resources)
  - [Guides and Analysis](#guides-and-analysis)
  - [Community Discussions](#community-discussions)
- [Third-Party Clients](#third-party-clients)
  - [Desktop Apps and Distributions](#desktop-apps-and-distributions)
  - [Terminal, Mobile, and Web Experiences](#terminal-mobile-and-web-experiences)
- [Selected Plugins](#selected-plugins)
  - [Workflows and Agents](#workflows-and-agents)
  - [Context, Sessions, and Input](#context-sessions-and-input)
  - [Browser, Vision, and Interface](#browser-vision-and-interface)
  - [Sandboxing and Execution](#sandboxing-and-execution)
  - [Themes and Skins](#themes-and-skins)
- [External Integrations](#external-integrations)
- [Developer Tools](#developer-tools)
- [Acknowledgements](#acknowledgements)

## Quick Start

[DeepSeek Harness](https://deepseek.com/harness/) (also known as DSH or `dsh`) is an open-source Agent Harness project from DeepSeek AI. Built on [Cordis](https://github.com/cordiverse/cordis), it follows an **Everything is a Plugin** architecture: model adapters, tools, session logs, interfaces, and the Agent Loop can all be composed and replaced through a plugin tree.

The latest verified official GitHub developer preview is [`0.1.2-rc.1`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.2-rc.1); both npm `latest` and `next` now point to `0.1.2-rc.1`. This RC adds full-history turn navigation, exact token / duration statistics, subagent model selection, ACP standard controls, schedules, connection retry, and replaces one-way `report` with continuable two-way `send_message`. Public WebFetch is enabled by default with SSRF protection; the SQLite Session backend was removed (old data is retained and requires an older version to export); DeepSeek adapter requests include enabled plugin package names and versions by default (configurable off), while incremental Session-log upload remains opt-in and off by default. The official release also states that DSH has not been security-audited and that Sandboxes, Approvals, and Permissions do not guarantee isolation. DSH versions shown below are only the development or test baselines claimed by project authors and must not be treated as automatic compatibility with the latest preview.

### Launch the Web UI

Install [Node.js](https://nodejs.org/) 22.19.x or 24+ (24+ recommended), then run:

```bash
npx @deepseek-ai/dsh web
```

Open `http://127.0.0.1:3080` by default. Configure a model provider under **Settings → Models**, then create a session. See the [official quick start](https://deepseek-harness.github.io/deepseek-harness/guide/quickstart) and [model provider guide](https://deepseek-harness.github.io/deepseek-harness/guide/providers) for details.

### Run from Source

```bash
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

### Use the Python SDK

The official Python SDK lets you call Harness programmatically through its bundled runtime, without requiring a system Node.js installation. It currently requires Python 3.10+. Refer to the [official Python SDK guide](https://deepseek-harness.github.io/deepseek-harness/guide/python-sdk) for supported platforms and current limitations.

```bash
python -m venv .venv
. .venv/bin/activate
python -m pip install deepseek-harness-sdk
```

### Install Plugins

`web` and `headless` are built-in distribution Profiles. External plugins join a target Profile as Bundles that declare `dsh.bundle`:

```bash
dsh plugin --profile web add <package-or-git-spec>
dsh --profile web --dump-config
```

When installing from a Git repository, pin a commit and inspect its installation scripts first. pnpm may require explicit approval for dependency build scripts, which execute outside the Agent sandbox. See the [official plugin packaging and installation guide](https://deepseek-harness.github.io/deepseek-harness/develop/basic/publish) for the complete mechanism.

## Official Resources

The official project provides an open-source repository, a companion paper, extensive reference documentation, and an actively maintained developer community.

### Packages and Integrations

- [@deepseek-ai/dsh](https://www.npmjs.com/package/@deepseek-ai/dsh): official npm launcher package for the CLI and Web UI
- [deepseek-harness-sdk](https://pypi.org/project/deepseek-harness-sdk/): official Python SDK for programmatic DSH integration

### Source Repositories

- [GitHub](https://github.com/deepseek-ai/deepseek-harness): source code, issues, releases, and contributors
- [Paper](https://github.com/cordiverse/paper): detailed paper on the Cordis-based product architecture

### Official Documentation

- [Chinese website](https://deepseek.com/harness/): product positioning and core concepts
- [Documentation](https://deepseek-harness.github.io/deepseek-harness/guide/quickstart): entry point for usage, plugin development, and architecture reference

### Community

- [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions): questions, usage discussions, and proposals
- [DeepSeek Discord](https://discord.gg/Ycq5dCaS4): official Discord community, primarily in Chinese
- ["DeepSeek Harness"](https://x.com/search?q=%22DeepSeek%20Harness%22%20OR%20dsh-plugin&src=typed_query&f=live): live X search results for DSH
- [# dsh-plugin](https://github.com/topics/dsh-plugin): DSH plugin projects on GitHub

## Community Resources

### Guides and Analysis

| Guide | Format | Coverage |
| --- | --- | --- |
| [DeepSeek Harness from Zero to One](https://yanhua1010.github.io/dsh-harness-tutorial/) | Chinese guide and demos | Covers concepts, source walkthroughs, eight demos, and a `mini-harness` teaching project |
| [DeepSeek Harness: From First Boot to Teardown](https://github.com/alchaincyf/deepseek-harness-orange-book) | Chinese hands-on ebook | Available as PDF, EPUB, and HTML, with the full system prompt, a 129-line default boot manifest, and three raw session logs |
| [Dissecting DeepSeek Harness](https://xueai.app/slides/learn.html#dsh-1.html) | Interactive source-code course | Breaks down sessions, context, tools, sandboxing, Code Mode, Subagents, and other core mechanisms |
| [What Cordis Is Doing, Seen Through DeepSeek Harness](https://blog.antinomie.org) | Chinese architecture essay | Explains the Cordis mental model from a plugin author's perspective and how complexity moves inside the system |
| [DeepSeek Harness Handbook](https://github.com/Electricitysheep/dsh-handbook) | Bilingual handbook | 14 chapters on install, plugin development, security, and cost, with online reading, PDFs, and runnable examples; content is CC BY-NC-SA 4.0 and based on `0.1.0-rc.6` |
| [NanoCordis](https://github.com/SheltonLiu-N/nano-cordis) | Runnable teaching implementation | Rebuilds the Cordis plugin framework and a DSH-shaped agent runtime in about 1,600 lines of TypeScript; MIT, npm `0.1.0`, and 95 tests. The default fake model needs no key, the Bash tool still asks for approval, and real-model credentials are read only from environment variables |

### Community Discussions

Public long-form social posts with substantial arguments, practical detail, or first-hand context that supplement gaps in official materials.

| Post | Author and Context | Summary |
| --- | --- | --- |
| [Understanding DSH from an Early Participant's Perspective](https://x.com/jiayuan_jy/status/2087911060154314963) | [Jiayuan (JY) Zhang](https://x.com/jiayuan_jy); the author reports receiving repository access one month early | Frames DSH as both a working Coding Agent and an Agent development framework; uses a “LEGO car” analogy for Everything is a Plugin and discusses runtime self-extension, early self-evolving software, current maturity, and functional-programming characteristics. |
| [Understanding DSH as an Agent Runtime / Agent OS](https://x.com/anion_ex/status/2087910193783025853) | [Anionex](https://x.com/anion_ex); private-beta participant and plugin author | Explains DSH through the composability of models, tools, policies, storage, context, interfaces, and Loops, then discusses limited Agent visibility into the runtime and controlled self-extension. |
| [After a Night with DeepSeek Harness, I Found It Challenging Claude Code the Minecraft Way](https://www.pingwest.com/a/316436) | PingWest; launch-night media observation | Maps DSH core, plugins, directories, and distributions to Minecraft vanilla, Mods, CurseForge, and modpacks, while recording launch-night compatibility and security debates. |
| [Reading DSH Against Codex: Declarative Plugins vs a Swappable Agent Loop](https://x.com/grapeot/status/2088019011561005382) | [鸭哥](https://x.com/grapeot); line-by-line source comparison with Codex. Expanded essay at [yage.ai](https://yage.ai/share/dsh-deep-analysis-20260813.html) | Contrasts Codex's declarative plugins with DSH's in-process imperative plugins, arguing that everyday coding does not need Cordis complexity; the one structural advantage is a hot-swappable Agent Loop that gives a self-evolving harness a physical slot. |

## Third-Party Clients

The following projects provide standalone user interfaces, distribution formats, or productized assemblies rather than a single tool capability.

> **Classification note:** Distributions and forks directly reuse, modify, or repackage the complete DSH Runtime and cannot be installed with `dsh plugin`, so they are not plugins. Standalone clients connect to DSH through Web, RPC, ACP, or companion bridge plugins. Both remain important parts of the Harness ecosystem.

### Desktop Apps and Distributions

| Project | Platform / Form | Description |
| --- | --- | --- |
| [DeepSeek Harness Desktop (anywhere-labs)](https://github.com/anywhere-labs/dsh-desktop) | macOS (Apple Silicon) / Windows · Electron | `v2.0.2` pins and runs DSH `0.1.1-rc.2` unchanged, with a local service, tray, recovery / rollback, and built-in plugin market; upstream breaking changes may invalidate old Profiles and unadapted plugins, so create a safe Profile and retain the plugin list before upgrading |
| [dsh-desktop](https://github.com/bruc3van/dsh-desktop) | macOS / Windows · Electron · Early | Reuses the official Web UI unchanged and keeps long-running tasks alive in the tray; disables renderer Node integration, restricts navigation, and verifies update packages with SHA-256, but the Agent process retains normal user-level file access and release packages are not formally developer-signed |
| [DeepSeek Harness Desktop (steven-kid)](https://github.com/steven-kid/deepseek-harness-desktop) | macOS / Windows / Linux · Electron · Early | Minimal shell that preserves the upstream Web UI, uses a random loopback port, Electron sandboxing, and `contextIsolation`, and smoke-tests packaged startup across platforms; macOS builds are not notarized and Windows builds are not commercially signed |
| [DeepSeek Harness Desktop App](https://github.com/vibeinging/dsh-desktop) | macOS / Windows · Electron · Community workbench | `v0.1.9` adds projects, Git Worktrees, a browser, Canvas, Sites, Office artifacts, file / folder attachments, and 14 pinned Bundles on the official Web / Profile runtime path. The macOS Apple Silicon package is signed and notarized; the Windows x64 package is unsigned but installation, startup, offline Profiles, recovery, uninstall, and residue cleanup passed on a GitHub Windows runner. Interrupted plugin installs retry safely on the next launch, while plugins deliberately removed by the user are not restored |
| [TinyWhale](https://github.com/aimierbear/TinyWhale) | macOS · Electron · Distribution fork | Directly forks `deepseek-ai/deepseek-harness` and adds a desktop shell; connects to an existing Web UI or launches a full `dsh web` Runtime, so it is not a plugin |
| [Oh-DSH](https://github.com/hust-open-atom-club/oh-dsh) | macOS / Linux / Windows · Community distribution | Packages DSH, Node.js, and local capabilities as Desktop, Web, and TUI editions with tiered installers and a unified `ohdsh` launcher |
| [DSH Desktop](https://github.com/dataelement/dsh-desktop) | macOS / Windows · Electron | Cross-platform desktop client for managing local Harness instances, workspaces, random ports, Profiles, plugins, and sessions |
| [dsh-launcher](https://github.com/Ruler4396/dsh-launcher) | Windows · WebView2 | Lightweight launcher with silent startup, a standalone window, portable packages, and MSI distribution |

### Terminal, Mobile, and Web Experiences

| Project | Type | Description |
| --- | --- | --- |
| [dsh-TUI](https://github.com/ccch1mneyyy/dsh-TUI) | TUI Bundle | Claude Code-style full-screen terminal, streaming status, context instruments, and session rollback |
| [dsh-tianshu-tui](https://github.com/huiliyi37/dsh-tianshu-tui) | TUI Bundle | Complete terminal interaction layer evolved from Tianshu, with state driven by the DSH session event stream |
| [dsh-tui](https://github.com/openguardrails/dsh-tui) | TUI Bundle · Early | Supports local DeepSeek and offline use; under active development, and the pre-port test suite is not yet running |
| [dsh-mini-tui](https://github.com/boxeryao/dsh-mini-tui) | TUI plugin · Early | Lightweight terminal UI connected directly to the DSH Runtime; MIT and `v0.2.0`, installed from npm and developed and tested against DSH `0.1.0-rc.6` |
| [Orbis](https://github.com/icodesign/orbis) | Mobile remote control · Beta | Uses a DSH plugin for device pairing, end-to-end encrypted transport, and real-time multi-device updates |
| [dsh-web-ui](https://github.com/zhu1090093659/dsh-web-ui) | Web UI collection | Collects task boards, Git Graph, mobile UI, skins, pets, runtime statistics, and other components |
| [dsh-web](https://github.com/Tom6814/dsh-web) | Docker Web · Early | Deploys a complete Web interface, workspace, and plugin market with Docker; development is moving quickly, and a data volume is required to persist configuration and sessions |

> Inclusion does not imply that a project is signed, notarized, self-contained, or production-ready. Check each project's README and Releases for current status.

## Selected Plugins

### Workflows and Agents

- [dsh-toolkit](https://github.com/omdsh-dev/dsh-toolkit): deterministic tools for time, encoding, JSON, calculations, CSV, regex, Markdown, Diff, and more.
- [dsh-deep-research](https://github.com/omdsh-dev/dsh-deep-research): adaptive deep-research orchestrator for DSH.
- [dsh-101](https://github.com/bill9109/dsh-101): learning mode for reading and understanding the official documentation inside DSH.
- [dsh-auto-approval](https://github.com/Andy8647/dsh-auto-approval): classifies tool calls with rules and models, then returns `allow / deny` approval decisions.
- [mstar-harness](https://github.com/btspoony/mstar-harness): Skill-driven Harness / Loop Engineering workflow plugin.
- [dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams): Agent Teams capabilities for DSH.
- [dsh-automation](https://github.com/titanwings/dsh-automation): runs scheduled standalone tasks in fresh root Agents and Sessions, preserving definition revisions, run history, and explicit workspace and permission boundaries.
- [dsh-plannotator](https://github.com/titanwings/dsh-plannotator): annotates Agent plans section by section and submits structured feedback, with draft isolation, version binding, and stale-plan rejection.
- [dsh-spec-collab](https://github.com/zx490336534/dsh-spec-collab): turns raw product requirements into Git-versioned Ready Specs co-reviewed by product, engineering, and both sides' AI; AI can submit Review Items and candidate patches, while humans retain confirmation and canonical-save authority. Apache-2.0 and npm `0.2.1`, declaring DSH `0.1.1-rc.1` compatibility and shipping a test suite; it is still a same-day fast-moving project with no CI, GitHub Release, or independent-use evidence, so it remains Early. The plugin writes a collaboration ledger and separate Git repository under `~/.dsh/spec-collab` and starts additional AI review Sessions; its HTTP management surface is loopback- and same-origin-only by default, pseudonyms are not authentication, and external exposure requires separate authentication plus a trusted reverse proxy.
- [dsh-context-guard](https://github.com/GreenLv/dsh-context-guard): captures requirements, prohibitions, acceptance criteria, and later corrections as a task contract, allows Goal / turn completion only when current successful evidence matches the current contract, and rebuilds or re-verifies certificates from native Session events. Apache-2.0, npm / Release `0.1.0`, pinned to DSH `0.1.1-rc.2`; the repository reports 104 tests plus native isolated acceptance on macOS and Windows. It appends no custom event types and is not a sandbox, memory system, or semantic proof engine; conservative command-effect parsing and evidence matching can still miss cases, and the same-day first release has no independent-use evidence, so marked Early.
- [dsh-record-replay](https://github.com/humblebanana/dsh-record-replay): records macOS desktop workflows and generates Skills; currently requires Xcode Command Line Tools and a separate local `open-record-replay` source checkout.
- [dsh-science-workbench](https://github.com/poplarity/dsh-science-workbench): reproducible science workbench that records cells, figures, feedback, and rerun lineage in a manifest, together with environment snapshots and input/output hashes; MIT and `v0.1.1`, still Early.
- [dsh-omicos](https://github.com/omicverse/dsh-omicos): connects OmicOS bioinformatics to DSH with a persistent Python / R kernel, capability catalog, background jobs, and live execution views; GPL-3.0-only and published to npm as `0.2.1`. Analysis tools run with `permission_mode: full` and may start a local kernel; cloud-backed models and higher tiers require an OmicOS account.
- [dsh-crew](https://github.com/ZSeven-W/dsh-crew): dispatches real DSH workers from Claude Code or Codex with progress reporting, status shards, and tier policies; MIT and Release / npm `next` `0.1.0-rc.4`, verified on DSH `0.1.1-rc.1` with MCP and package smoke checks. It writes to `~/.config/dsh-crew/status.d/`, and external model services may require API keys; it remains a prerelease without separate test CI, so it is marked Early.
- [dsh-trading](https://github.com/maddogfinance/dsh-trading): DSH workbench for trading research with deterministic indicators, CSV providers, and interactive charts; MIT and npm `@dsh-trading/bundle@0.1.0`. It exposes no order-execution interface and heuristically blocks fund-moving tools, but that filter is not a complete security boundary, so the project is marked Early.
- [oh-story-dsh](https://github.com/worldwonderer/oh-story-dsh): brings 13 novel-writing Skills, seven specialist Roles, and a short-drama production workflow into native DSH Sessions, approvals, and a three-column creative workbench. MIT, npm / Release `0.1.3`, Node.js 24+, and peer dependencies starting at DSH `0.1.1-rc.1`; the Release reports 34 automated tests and Ubuntu / macOS / Windows CI. This version reuses the official Composer height, adds a scroll safety area and anchor-geometry regression coverage, and keeps expanded tasks, streaming state, and located messages above the Composer. The build excludes upstream login / CDP scrapers and the standalone dashboard. The plugin does not read model credentials or open its own listener, but it can read and write creative-project files and invoke specialist Roles within the calling Agent's visible tools, and it adds a DSH Web Server file route protected by Host, Origin, Session, path-containment, and optimistic-concurrency checks. First released on August 21 and explicitly verified only on DSH rc.1, it still lacks long-term maintenance and independent-usage evidence, so it is marked Early.

### Context, Sessions, and Input

- [dsh-context](https://github.com/bowenliang123/dsh-context): shows the per-request token composition of system prompts, tool schemas, messages, injections, replies, and tool results in a Web UI Context panel and `/context` command, including compaction, pruning, and cache-hit signals; Apache-2.0 and npm / Release `0.35.0`. Recent releases add an Agent Network that links to subagents at any depth, while File Activity now understands nested PTC / Code Mode calls, incomplete logs, and read-line footprints. When the Host explicitly advertises `canOpenPath`, file names can be handed to the system default application; workspace paths resolve against the Session root, and unprovable rows such as search patterns are never openable. Peer dependencies still start at `^0.1.0-rc.7`; source tests use per-file coverage gates and a Bundle smoke test. No external service is required, though the UI checks npm at most hourly and falls back to npmmirror when the official Registry is unavailable.
- [dsh-profile-settings](https://github.com/XMoon/dsh-profile-settings): adds a per-Profile `settings.patch.yml` overlay above global `settings.yaml`, with recursive merges, `!unset`, source inspection, hot reload, and Settings-page management while preserving the existing `ctx.settings` interface. MIT, npm / Git tag `0.1.0`, Node.js 22.6+, and peer dependencies pinned to the DSH `0.1.1-rc.2` family, with 15 test files; the latest CI passed source checks, build, and release-tarball smoke tests on Node 22.6 / 24 / 26, but the overall workflow still failed at npm publication even though Registry already serves `0.1.0`. The plugin writes the Profile overlay by default, while `promote` / `demote` / `migrate` can also change values across global and Profile documents under locks, atomic replacement, and migration backups; it launched the same day with no GitHub Release or independent usage evidence, so marked Early.
- [dsh-context-doctor](https://github.com/Zhenyu98/dsh-context-doctor): audits the context-token cost and conflicts of AGENTS.md, Skill directories, and tool Schemas.
- [dsh-memory-evolve](https://github.com/csyangwen/dsh-memory-evolve): cross-session memory, background evolution, and branch-aware behavior.
- [dsh-noema](https://github.com/ZSeven-W/dsh-noema): connects DSH to local-first Noema long-term memory, with recall-before-work, a settings page, and import from Codex, Claude Code, Cursor, Hermes, and other tools; MIT and Release / npm `next` `0.1.0-rc.3`, verified on DSH `0.1.1-rc.1` with CI and tests, still new and marked Early.
- [EverOS Memory for DSH](https://github.com/EverMind-AI/EverOS/tree/main/examples/dsh): captures user, assistant, tool-call, and tool-result trajectories into local EverOS and recalls them before later sessions; Apache-2.0, plugin `0.1.0`, supporting DSH `>=0.1.0-rc.6 <0.2.0-0`. It is not yet on npm, and deferred extraction still depends on an untagged EverOS capability. Trajectories may contain source, commands, and tool output, so external-model configuration needs a separate review; marked Early.
- [dsh-at-file](https://github.com/omdsh-dev/dsh-at-file): searches workspace files with `@file` in the composer and attaches their content.
- [dsh-shikitor](https://github.com/oneworks-ai/shikitor/tree/master/packages/dsh-shikitor): unifies discovery of `#` sessions, `@` workspace files, `$` Skills, and `/` commands in the composer and adds an extensible workspace file editor; MIT and npm `1.0.2`, supporting DSH `>=0.1.0-rc.5 <0.2.0`. Edits auto-save by default, while appearance and path rules are stored in the browser.
- [dsh-message-edit](https://github.com/Moeblack/dsh-message-edit): branch-based message editing, retry, regeneration, and version timelines.
- [dsh-client-auto-retry](https://github.com/Frog755/dsh-client-auto-retry): automatically sends the default message `继续` to the original session after `error`, `interrupted`, or `max-tokens`, bounded by a grace period, cooldown, and consecutive-retry cap; MIT and npm `0.3.1`, with compatibility claimed only for DSH `0.1.0-rc.7`. It scans interrupted sessions from the last 15 minutes on startup by default and may continue model calls and token usage; no visible tests or Release, so marked Early.
- [dsh-prompt-studio](https://github.com/Moeblack/dsh-prompt-studio): edits system-prompt fragments with a live preview.
- [dsh-turn-rewind](https://github.com/Anionex/dsh-turn-rewind): rewinds conversations and workspace state through a persistent Change Ledger.
- [dsh-filesnap](https://github.com/extracurricular-ai/dsh-filesnap): rewinds the conversation and workspace files to an explicitly selected turn, always restoring into a new fork with a rescue point created first and `/redo` available to reverse the rewind, without changing Git branches, commits, stashes, or worktrees. Apache-2.0, npm / Release `0.2.1`, Node.js `^22.19` or 24+, and Linux / macOS / Windows on x64 or arm64; CI builds the current DSH from source and runs ten test files plus the client build. Its bundled Rust `filesnap` binary captures binaries, ignored files, and observed out-of-workspace `ctx.fs` paths; restore can overwrite files or delete them only against explicit tombstones, while snapshots remain unencrypted under the current user's platform data directory. Uninstalling makes captured Sessions with custom events unreadable until the plugin is reinstalled; it launched the same day with no independent usage evidence, so marked Early.
- [dsh-compaction-instant](https://github.com/KitDoesIt/dsh-compaction-instant): replaces LLM summarization with deterministic compilation and restores compressed content through `recall` / `search`; replacing the built-in compactor requires an npm alias and is a deeper runtime modification.
- [toolshrink](https://github.com/unclecode/toolshrink): performs content-aware reduction for test, diff, JSON, tree, log, and install output while retaining references to originals when needed; MIT `0.1.0`. It currently requires a source build and an edit to the global `~/.dsh/cordis.patch.yml`; stored originals are removed after 24 hours, so it is marked Early.
- [dsh-tool-squeeze](https://github.com/w2829562572-dev/dsh-tool-squeeze): provides deterministic, local-first compression for test, diff, JSON, tree, log, install, and HTML tool output; MIT `v0.1.0`, pinned to DSH / `dsh-tools` `0.1.0-rc.8`, with 21 tests and reproducible benchmarks reported by the project. Unlike toolshrink's source build and plugin-owned retention, it installs directly as a GitHub bundle, makes no extra model or network call, and delegates the full original to the official spill store; compression remains lossy, and the same-day initial release has no CI or independent-use evidence, so it is marked Early.
- [dsh-whale-report](https://github.com/SenmuuuuW/dsh-whale-report): generates daily, weekly, monthly, yearly, and custom-range reports from session event logs; MIT, Release / npm `0.6.1`, Node.js `^22.19 || >=24`, with DSH peers constrained to `>=0.1.1-rc.2 <0.2.0`. Version 0.6.0 adds the first strictly allowlisted Apply & Verify action: only after repeated Bash-timeout evidence and explicit user approval may it propose changing `shell.timeoutMs` from 60 to 120 seconds, then verify, audit, and safely roll back; it supports no arbitrary settings, arbitrary commands, auto-healing, or automatic rollback. The release commit's CI passes, and the release reports 393 tests plus real-package acceptance. Version 0.6.1 corrects historical pricing effective dates, post-startup session reconciliation, and resumed-session accounting, which can materially change historical token / cost totals without changing the Apply & Verify boundary. The project remains new and now has a constrained settings-write path, so it is marked Early.

### Browser, Vision, and Interface

- [dsh-browser](https://github.com/Lum1104/dsh-browser): Chrome sidebar extension that lets DSH operate the current browser page directly.
- [dsh-vision-toolkit](https://github.com/Anionex/dsh-vision-toolkit): image Q&A, long-screenshot OCR, UI reconstruction, grounding, and pixel comparison.
- [dsh-computer-use](https://github.com/Anionex/dsh-computer-use): native macOS Computer Use Bundle that prioritizes Accessibility, rejects stale observations, and scopes permissions by app, Session, and action; currently an early `0.1.0` release installed from a source checkout.
- [dsh-plugin-appshot](https://github.com/TaurusWood/dsh-plugin-appshot): captures the current foreground window through a macOS / Windows global shortcut and attaches it to the active DSH Composer; MIT, npm / Release `0.4.1`, with a fix for building the native agent on macOS 14+ plus 34 test paths and native builds for both platforms. The prebuilt package includes a macOS app and self-contained Windows EXE; macOS requires Screen Recording and Accessibility permissions, while the native agent persists screenshots and hands them to the Host over local SSE. Package metadata declares no peer dependencies and development still pins old DSH `0.1.0-rc.6`; current Alpha compatibility and the high-permission path still need real-device revalidation, so marked Early.
- [dsh-ios](https://github.com/ZSeven-W/dsh-ios): brings a live iOS Simulator or USB-connected iPhone into DSH conversations with 22 tools for build-and-run, semantic UI automation, SwiftUI Preview hot reload, logs, backtraces, and leak checks; MIT and Release / npm `latest` / `next` `0.1.0-rc.5`, with passing Plugin Check and release workflows on the Release Commit and 744 self-reported verification steps. rc.5 adds fast timeouts, a ten-second cooldown, and a shared size cache for busy WDA devices, plus an eight-second watchdog for stalled MJPEG streams, although the original real-device failure was not reproduced on hardware. Package peers start at DSH `0.1.0-rc.6` and the Requirements say `>=0.1.0-rc.6`, while the README header still carries stale rc.3 / tested-on-DSH-`0.1.1-rc.1` text, so compatibility metadata is not yet consistent. It remains a prerelease requiring macOS with full Xcode; optional AXe may download a SHA-256-verified binary, OCR compiles locally, real-device control requires a user-provided signed WebDriverAgent, and the tools can build software and act on a physical device, so it is marked Early.
- [dsh-android](https://github.com/ZSeven-W/dsh-android): brings a live Android emulator or USB phone into DSH conversations with 20 tools for discovery, build-and-install, semantic / OCR UI control, logs, processes, and memory. MIT and Release / npm `next` `0.1.0-rc.4`, verified on DSH `0.1.1-rc.1` and Node.js 24.11+, with seven static smoke suites and passing CI; it remains Early because it launched the same day, every Release is a prerelease, npm `latest` still points to rc.1, and rc.4 must be installed explicitly from `@next`. Runtime use requires adb / Android SDK, and the tools can build and install APKs, control devices, and read logs; OCR is macOS-only and locally compiles the bundled Swift helper on first use, while browser routes use loopback fences and short-lived HMAC capabilities.
- [modlens](https://github.com/liustack/modlens): gives text-only models vision through pasted images and model routing, offering an alternative to standalone vision tools that process workspace images.
- [ModSearch](https://github.com/liustack/modsearch): adds Web search, X search, and focused page reading to DSH with structured evidence; MIT and released as `v5.9.1`, with multi-key rotation within one engine and a fix for Windows automatic routing that previously searched only for extensionless commands and missed native `.exe` CLIs. It retains SSRF and DNS-rebinding defenses for local fetching; individual engines may require external CLIs, sign-in, API keys, quotas, and their own service terms.
- [dsh-better-browser](https://github.com/titanwings/dsh-better-browser): controls a real browser with retained login state through the external Kimi WebBridge and maintains tab sessions per task; requires WebBridge to be installed and running separately.
- [dsh-web-review](https://github.com/CanglongCl/dsh-web-review): previews pages inside DSH, lets users select elements, and submits selectors, accessible names, and change intent; includes a real frontend-modification eval suite, but currently declares no license.
- [dsh-mcp-apps](https://github.com/sugarforever/dsh-mcp-apps): turns DSH Web into an MCP Apps Host and renders interactive Apps in sandboxed iframes with CSP and Permission Policy controls; MIT and `v0.1.1`, but still new and marked Early.
- [dsh-genui](https://github.com/omdsh-dev/dsh-genui): renders charts, forms, Mermaid diagrams, 3D scenes, and other interactive components in replies, then sends action events back to the model; MIT, source package version `0.9.1` with latest GitHub Release `v0.8.6`, mainly Git-installed, with peer ranges covering DSH rc.8 and `0.1.1-rc.x` plus CI, so it remains Early.
- [DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar): sidebar workbench integrating files, terminal, Git, Subagents, and third-party tabs.
- [dsh-openpencil](https://github.com/ZSeven-W/dsh-openpencil): previews and edits OpenPencil designs inside DSH.
- [dsh-visualize](https://github.com/Nagi-ovo/dsh-visualize): generates sandboxed, interactive HTML cards in the conversation stream.
- [dsh-notification](https://github.com/omdsh-dev/dsh-notification): configurable desktop notifications based on task outcomes and keywords.
- [dsh-locale-ja](https://github.com/fang2hou/dsh-locale-ja): adds a Japanese DSH Web interface and system Japanese fonts across 29 namespaces and 721 UI strings. It is MIT, npm / Release `0.4.3`, Node.js 22+, and pins `@deepseek-ai/dsh-client-locale ^0.1.1-rc.2`; repository tests, dictionary-drift checks, and daily E2E against DSH `next` pass. It mounts only a client localization module, adding no Host route, credential, or external service.
- [dsh-share](https://github.com/hellodigua/dsh-share): generates and shares DSH conversation content in one click.

### Sandboxing and Execution

- [sandbox-micro](https://github.com/omdsh-dev/sandbox-micro): provides a fail-closed microsandbox microVM capability; both the Provider and model-facing tools stay disabled after installation until separately enabled, and failed platform checks never degrade to unconstrained host execution. It has test directories but no formal Release; `package.json` declares BSD-3-Clause, but the repository has no root `LICENSE` file, so it is marked Early.
- [dsh-credentials-keyring](https://github.com/irisnb/dsh-credentials-keyring): replaces plaintext credential files with Windows Credential Manager, macOS Keychain, or Linux Secret Service, and fails closed on Linux without Secret Service; MIT `0.1.0`, with in-memory backend tests but no npm package or Release yet. Real OS keychains still need per-platform smoke tests, so it is marked Early.
- [dsh-win32](https://github.com/sjh9714/dsh-win32): diagnostics, acceptance, and safe repairs for current DSH on Windows; MIT and npm / Release `0.17.0`, with CI covering npm-hoisted and pnpm-strict installs on Node 22.19 / 24. The new `verify` command uses the installed official PowerShell, subprocess, and Workspace Write components inside an isolated temporary home/workspace to check persistent state, outside-write denial, recovery, cancellation, PTY replacement, and cleanup, but it does not boot the full Minimal host or make a model request. Default `setup` does not replace the official stack; it checks components, repairs only provably broken `koffi` loading, and can create a desktop shortcut. `doctor` is read-only and `fix` only repairs known-broken or genuinely unloadable `koffi`. Legacy Git Bash / BusyBox paths remain behind explicit `setup --legacy`, where Git Bash requires `danger-full-access`; the tool does not automatically install Git, PowerShell, BusyBox, WSL, or another DSH bundle.
- [dsh-exec-extension](https://github.com/LvDAO/dsh-exec-extension): adds a one-shot Exec CLI to a Headless profile, exposing stdin, `@file`, cwd, model, timeout, JSONL output, and permission mode as per-invocation flags; MIT `v0.1.0`, pinned to DSH `0.1.0-rc.7` and Node.js 22.19+, with Node / Rust tests and CI. The default remains `workspace-write`, and UI-less `--approval ask` fails closed; `--full-auto` / `--yolo` auto-approve, while only an explicit `--sandbox danger-full-access` removes sandboxing. It currently installs from a pinned Git tag, whose dependency `prepare` runs outside the Agent sandbox and should be reviewed and explicitly approved first.

### Themes and Skins

- [dsh-deep-whale](https://github.com/Small-tailqwq/dsh-deep-whale): whale-girl theme collection for the DSH Web GUI; currently includes the hot-pluggable `maid-atelier` Web Client Bundle, installable and removable with `dsh plugin --profile web add ...`. Licensed under **CC BY-NC-SA 4.0**, which prohibits commercial use.

## External Integrations

- [dsh-oomol](https://github.com/oomol-lab/dsh-oomol): progressively discovers apps and actions through OOMOL Connector, inspects schemas, and executes connected SaaS capabilities; MIT and npm `0.1.4`. DSH stores only a revocable OOMOL MCP key while third-party OAuth tokens remain in OOMOL; removing the plugin does not disconnect provider accounts, and action execution currently has no idempotency key.
- [Tencent Cloud ADP for DSH](https://github.com/TencentCloudADP/Tencent-ADP-dsh-plugin): Tencent Cloud ADP's maintained integration for models, Hunyuan AI search, the API / MCP plugin marketplace, Skill plaza, and published ADP apps. It is MIT, npm / Release `0.1.1`, and Node.js 22.19+ or 24+; simulated HTTP tests gate CI, while real-account tests run only with an explicit environment. Tool Key, SecretId / SecretKey, and per-app AppKey are three separate credential planes whose values live in DSH Credentials or environment variables. App / Agent / Release mutations register only when `allowMutating` is enabled and still require approval. The version is early, depends on an external Cloud account, and can mutate ADP resources, so it is marked Early.
- [dsh-forge](https://github.com/maxmilian/dsh-forge): read-only tools for instances, repositories, issues, branches, pull requests, Actions runs, and job logs on self-hosted Gitea and Forgejo. It is MIT and npm / Release `0.3.3`, supports DSH Tools rc.6 and current rc.2, and runs live integration CI against official Gitea / Forgejo and Runner containers. Use the narrowest read-only token through an environment variable. npm and the prebuilt Release do not build locally; a Git-source install runs `prepare`, so review and pin the commit before granting that permission.
- [dsh-sonarqube](https://github.com/maxmilian/dsh-sonarqube): read-only access to SonarQube Community Build Quality Gates, issues, Security Hotspots, coverage, and duplication. It is MIT and npm / Release `0.1.0`; peer dependencies cover DSH Tools rc.8 and current rc.2, and CI, coverage gates, and a live SonarQube `26.8.0.126808` check pass. Put the token in an environment variable; the plugin does not return or log it. This is still the first release, and the live instance exposed no successful Hotspot sample, leaving that path covered only by mocks, so it is marked Early.
- [Milvus for DSH](https://github.com/zilliztech/dsh-milvus): Zilliz-maintained, read-only Milvus / Zilliz Cloud integration for collections, schemas, exact lookup, scalar queries, and Dense, BM25, and Hybrid Search. It is Apache-2.0 and npm `0.1.3`, pinned to DSH rc.7. Milvus tokens and embedding keys live in write-only DSH Credentials, and query vectors are generated only in Host memory before being sent to Milvus. The repository has unit and explicitly network-gated integration tests but no GitHub Release or visible CI; operators must still verify the external endpoint, provider key, and longer-term compatibility, so it is marked Early.
- [Ollama](https://github.com/ollama/ollama/blob/main/docs/integrations/deepseek-harness.mdx): Ollama's official launcher for DSH, not a DeepSeek-official distribution. Use `ollama launch dsh` to install and start DSH, choose an Ollama model, and configure Web search; settings are stored separately in `~/.ollama/launch/dsh/settings.yaml` and do not modify `~/.dsh/settings.yaml`. Currently marked as a developer preview.
- [Rapid-MLX DSH Provider](https://github.com/raullenchai/rapid-mlx-dsh-provider): reads model capabilities, reasoning modes, and context windows from a local Rapid-MLX `/v1/models` endpoint instead of duplicating provider metadata in DSH; Apache-2.0, end-to-end verified on DSH `0.1.0-rc.7` with protocol tests, but deliberately kept as an unpublished source install, so marked Early. The default connection is loopback-only, Rapid-MLX must run separately, and image input fails explicitly.
- [Sealos Skills](https://github.com/labring/sealos-skills): a DSH Profile Bundle maintained by the Sealos team, providing eight cloud-native Skills for application deployment, databases, object storage, and related workflows. Actual use changes external Sealos Cloud resources and requires an account and relevant credentials; login writes `~/.sealos/kubeconfig`, and some flows require a relaxed sandbox. `package.json` declares MIT, but the repository currently has no root `LICENSE` file.
- [Nowledge Mem](https://mem.nowledge.co/integrations/deepseek-harness): adds Working Memory, prompt-time retrieval, MCP tools, and session capture to DSH; depends on the external Nowledge Mem product and `nmem` CLI and should be evaluated separately from open-source plugins.
- [Open Design](https://github.com/nexu-io/open-design): local-first open-source design application with a native DSH runtime adapter for structured streaming, model discovery, cancellation, and session resume; Apache-2.0 and a large standalone product rather than an ordinary plugin.
- [HarnessRouter](https://github.com/HarnessRouter/harnessrouter): self-hosted container exposing Codex, Claude Code, Hermes, Pi, and DSH through one local UHP API and console rather than acting as an ordinary DSH plugin. It is Apache-2.0 at Release `v0.9.1`, with Gateway, Runner, and UHP conformance tests plus dedicated security documentation; the DSH backend pins Python SDK / Runtime `0.1.0rc7` and refuses an internal JSON-RPC Server version other than `0.1.0-rc.7`. First start installs each Harness CLI from upstream under its own license, while a Docker volume persists the database, files, workspaces, and secret material. The console binds to loopback by default but starts with a default password that must be changed, with TLS added, before exposure. The container starts as root and drops privileges, Agents use per-Session users, and provider keys stay in a loopback relay process rather than the DSH environment. The project is new; its DSH adapter overrides private internal fields and rewrites selected streaming tool-call deltas, the pinned Runtime does not yet bundle the MCP client, and current official DSH `0.1.1-rc.2` is unverified, so it is marked Early.
- [dsh-multica-runtime](https://github.com/forrestchang/dsh-multica-runtime): early runtime bridge connecting Multica and DSH; the package is currently marked `private` and `UNLICENSED`, with incomplete installation and distribution boundaries.
- [dsh-imessage](https://github.com/photon-hq/dsh-imessage): turns one-to-one iMessage text sent to a Photon-hosted number into DSH prompts and returns final answers, with session switching, cancellation, approvals, and question replies; MIT and npm / Release `0.2.0`, pinned to DSH `0.1.0-rc.6`, with tests and CI. It requires a Photon account, a sender phone number, and host-only local credentials, and messages transit Photon; disconnect clears only local state and does not remove Photon cloud resources. The project is new and hosted-service-dependent, so it is marked Early.
- [dsh-lark-bot](https://github.com/PlutoKeating/dsh-lark-bot): connects local DSH to Feishu / Lark with streaming cards, workspaces, session recovery, and approvals; licensed under AGPL-3.0, with app credentials stored locally in plaintext configuration protected by mode `600`.
- [dsh-lark](https://github.com/sugarforever/dsh-lark): connects DSH to Feishu / Lark through the official Node SDK and a WebSocket connection, without a public callback endpoint; MIT and npm / GitHub `v0.1.1`. It requests only three message scopes by default and reads credentials from environment variables; actual use receives and sends external messages as the bot.
- [dsh-qqbot](https://github.com/tencent-connect/dsh-qqbot): Tencent-maintained QQ Bot plugin with QR-code binding, isolated direct/group sessions, and restart recovery; MIT and `0.1.0`, with credentials saved to the local Profile during binding.
- [dsh-im](https://github.com/xmanrui/dsh-im): manages ten IM channels and AI Office, with multiple bots, streaming replies, workspace / Session binding, remote approvals, and deferred task delivery. It is MIT, npm / Release `4.20.0`, and Node.js 22.19+, with passing CI at the release commit. The release supports unmodified upstream DSH `0.1.5-alpha.1` and the four previously supported DSH Web profiles; management uses Connection's public `/api` Fetch interface, without modifying or rebuilding DSH. Management is loopback-only by default; `trusted-host` still relies on DSH browser authentication and Host / Origin checks, while update and inbound-TTL management are always loopback-only. Restart the Host and refresh Settings after upgrade; authorized chat users can still invoke models and tools, and workspace / Session listings may expose local paths and sensitive metadata, so access must remain limited to trusted users.
- [LoongSuite DSH Plugin](https://github.com/loongsuite/dsh-plugin): converts Agent turns, model calls, tool executions, and token usage into OpenTelemetry GenAI traces for OTLP backends such as Jaeger, Tempo, SigNoz, and Langfuse; Apache-2.0 and Beta, tested with DSH `0.1.0-rc.6` in headless and Web profiles. Content capture is off by default; enabling it may export source code, credentials, and personal data.
- [Tencent Cloud Agent Observability for DSH](https://github.com/TencentCloud/tencentcloud-agentobs-sdk-dsh): Tencent Cloud-maintained direct-to-CLS observability plugin that maps sessions, agent loops, model streams, and tool lifecycles into five trace levels without an OTLP collector; Apache-2.0, npm / Release `0.0.1`, supporting DSH `>=0.1.0-rc.6 <0.2.0`. It is very new and marked Early. Prompt, response, and tool argument/result capture is on by default, so disable `captureContent` and set least-privilege access and retention before using sensitive repositories.
- [Token Monitor](https://github.com/Javis603/token-monitor): a local-first cross-platform desktop usage tool; the current Release is `v0.47.0`, while DSH JSONL / Zstandard session reading and per-turn token, prompt, and tool-record views arrived in `v0.46.0`. It is MIT; macOS builds are signed and notarized, Windows builds are signed, and DSH parsers have tests and CI. It sends no maintainer telemetry by default; optional multi-device sync sends aggregate usage and account / project metadata to an operator-chosen hub, but not raw prompts, source code, or credentials.
- [dsh-wakatime](https://github.com/dingyi222666/dsh-wakatime): reports DSH file activity, AI line changes, and project time to WakaTime; MIT and npm `0.1.1`, with tests but still new and marked Early. It requires a WakaTime API key, writes state under `~/.wakatime/dsh-wakatime/`, and automatically downloads or updates `wakatime-cli` when absent.

## Developer Tools

- [dsh-plugin-check](https://github.com/omdsh-dev/dsh-plugin-check): checks Manifests, Patches, build traps, and directory inclusion status.
- [DShScan](https://github.com/shaoshi20/dshscan): produces rule evidence, risk scores, and install advice for DSH plugins; it can scan local content offline, or explicitly fetch GitHub/npm source, run `npm audit`, or call an external LLM. MIT and npm / Release `0.5.0`, with CI and tests for DSH-specific rules, but still pinned to DSH `0.1.0-rc.6` and iterating rapidly, so marked Early. A low-risk result is not a security audit.
- [DSH Plugin Upgrade Skill](https://github.com/oh-my-dsh/dsh-plugin-upgrade-skill): provides eight Skills for DSH plugin upgrade, migration, authoring, testing, release, audit, and runtime debugging, with 45 migration cards through `0.1.2-alpha.4`, 12 general strategies, 29 Harbor benchmark tasks, and multiple with-versus-without-Skill evaluations. It is MIT, installs with `npx skills add oh-my-dsh/dsh-plugin-upgrade-skill`, and currently has passing validation CI. The unified entry recommends a read-only health check first and separates phases with confirmation, but focused workflows can edit source, install dependencies, run tests / Docker, package, and publish, so they require matching authorization. Created on August 30, 2026, it has no Release yet and its migration cards do not cover current `0.1.2-rc.1`, so it is marked Early.
- [DSH Harbor](https://github.com/ZSeven-W/dsh-harbor): builds a 13-class declared-versus-detected capability ledger for installed plugins, with `file:line` evidence, runtime ownership for tools / providers / routes, same-Profile conflicts, cross-Profile version drift, and change snapshots. It is MIT and npm `next` / Git tag `0.1.0-rc.2`, tested on DSH `0.1.1-rc.2`, with Node 20 / 24, Ubuntu / Windows CI and a real package smoke test. Default scanning is offline and read-only; snapshots write to `~/.config/dsh-harbor/`, and only an explicit upstream check reads npm registry configuration and uses the network, with credentials redacted from errors. It is not a sandbox, install gate, or policy engine, and remains a prerelease without a GitHub Release or independent usage evidence, so it is marked Early.
- [HOL Guard for DSH](https://github.com/hashgraph-online/hol-guard-plugin): applies fail-closed local policy checks at both DSH's asynchronous `tools/pre-execute` layer and its final monotonic Guard, routes ambiguous decisions through one-time native approvals, and keeps security receipts; Apache-2.0, Release `v0.3.0`, Node.js 20+, and a separately installed `hol-guard >=2.0.1024`. The repository has 14 test files, and CI includes a real headless denial test against pinned official DSH `0.1.0-rc.5` source; no Cloud account is required by default, while Cloud sync is optional. Installation changes selected Profiles, policy may block tool execution and wait in a local Approval Center, and coverage is limited to calls traversing DSH `ToolRuntime`, not code a plugin runs outside that pipeline. It is marked Early because compatibility with the current official `0.1.1-rc.2` is not yet proven and the latest runtime-version sync Workflow is failing.
- [dsh-fail-logger](https://github.com/Areium/dsh-fail-logger): redacts, deduplicates, and categorizes tool failures into a machine-maintained Skill record; it records problems without changing behavior automatically.
- [dsh-session-surgeon](https://github.com/xiaoshenming/dsh-session-surgeon): scans, inspects, exports, and repairs DSH sessions that fail to load, have sequence gaps, or retain temporary files; MIT `v0.1.0`, supporting DSH `0.1.0-rc.6` and installed from GitHub source, so marked Early. Repair defaults to dry-run, `--apply` writes a `.bak.<utc>` first, and export redacts by default unless `--no-redact` explicitly disables protection.
- [deepseek-harness-action](https://github.com/Lixiaoyiao/deepseek-harness-action): uses DSH in GitHub Actions for PR review, CI diagnosis, automated fixes, and Issue-to-PR workflows; write access is off by default, and validation runs in a credential-free container.
- [Awesome DSH Plugins Radar](https://github.com/AdamPlatin123/awesome-dsh-plugins): automated compatibility radar separating discovery, static, compile, and runtime signals; MIT, fast-changing, and without a Release, while “runtime usable” is not a security audit or quality guarantee, so marked Early.
- [dsh-market](https://github.com/dsh-market/dsh-market): in-DSH plugin market for browsing, searching, installing, updating, and uninstalling projects listed by `awesome-dsh-plugin`; MIT and npm / Release `v1.31.1`. On top of region-aware routing, mainland-China mirrors, official-source fallback, and Anywhere Labs Desktop's recoverable boundary, it explains when an npm-only Desktop cannot install a GitHub-only project, when a catalog path has disappeared, and which boot prerequisites remain after restore, rollback, or an operation. Version 1.29.3 rolls back both the dependency and Bundle row, and the Tasks panel survives closing Settings. It still compares whole-Profile Bundle state and syntax-checks CJS while skipping ESM syntax checks. Build scripts remain blocked by default, installation is same-origin POST only, and updates are blocked during Agent runs, but proxy transport does not prove byte equivalence and directory inclusion is not a security endorsement.
- [dsh-suite](https://whyihaveyou.github.io/dsh-suite/): bilingual DSH ecosystem index with plugin search, a `create-dsh-plugin` scaffolder, and basic compatibility metadata; its catalog refreshes hourly and it installs listed packages into a temporary Profile for daily compatibility checks. A successful install is not a security audit or quality guarantee.
- [dsplugin.app](https://dsplugin.app/): unofficial community DeepSeek Harness plugin directory / registry; review source and Manifest/`dsh.bundle` before install.
- [deepseek-harness-plugin-mcp](https://github.com/bobleer/deepseek-harness-plugin-mcp): lets other Agents discover, inspect, install, and invoke DSH plugins through MCP; installation and runtime are disabled by default and produce their respective side effects only when `--allow-install` / `--allow-runtime` is explicitly enabled.
- [dsh-payload-capture](https://github.com/Moeblack/dsh-payload-capture): captures and stores outbound model API Payloads for request-assembly debugging.
- [dsh-custom-tool](https://github.com/omdsh-dev/dsh-custom-tool): creates and manages sandboxed JavaScript tools through a Monaco editor.
- [dsh-open-in-vscode](https://github.com/omdsh-dev/dsh-open-in-vscode): opens the current workspace directly in VS Code from the Web UI.
- [dsh-movein](https://github.com/sjh9714/dsh-movein): moves Claude Code Skills, MCP servers, hooks, and global instructions into DSH with one command; dry-run by default, `CLAUDE.md` is read natively, and session history is out of scope. MIT, verified on DSH `0.1.0-rc.6`, still new and marked Early.
- [dshpack](https://github.com/hili986/dshpack): packages Skills, MCP servers, Profile patches, and permission defaults into installable, shareable, auditable DSH Profiles; MIT and npm `0.3.0`, with all 18 commands now available, including `init`, `export`, `compose`, `lock`, `pack`, transactional install / update / uninstall, and a loopback management UI. Build scripts are denied by default, sources are commit-pinned, exports get three credential scans, conflicts require explicit resolution, and journaled failures roll back. `doctor` may cause DSH to rewrite `cordis.yml` and dshpack itself writes audit logs. The Pack format and CLI remain unstable APIs, so marked Early.
- [hooks-adapter](https://github.com/JohnXu22786/hooks-adapter): lets DSH reuse Claude Code, Codex, and OpenCode hooks configs directly, with Shell, Webhook, LLM, and Subagent handlers; MIT, claiming 111 repository tests but no Release yet. Auto-discovered hooks can execute commands and transmit data, so it is marked Early.

## Acknowledgements

Thanks to the DeepSeek Harness team, the Cordis community, the first private-beta developers, and everyone contributing public documentation, plugins, clients, practical experience, and ecosystem indexes.

[![Liang Evolution Slider: current state Liangzi; click to open the full interactive version](assets/media/liang-intensity-calibrator-card-liangzi.png)](https://lichtspektrum.github.io/liang-intensity-calibrator/)
