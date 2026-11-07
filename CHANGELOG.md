# Changelog

All notable changes to **Visio Creator** are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2026-11-07

### Added & Released (Official Production Release)
- **Official Production Release**: First official production release published to `LazyAutomatar/Visio-Creator`.
- **Public Release Pipeline & CI/CD Parity**: GitHub Actions automated release pipeline (`release.yml`) cross-compiling, Authenticode signing, packaging, and publishing to LazyAutomatar.
- **Skia Vector Topology Canvas Parity**: Complete visual and interactive parity with Network Health Reporter (infinite workspace, 5px role stripes, wire-centered port badges, dynamic right-angle link routing).
- **Multi-Node Group Operations**: Synchronized group dragging, marquee box selection (AABB intersection), and keyboard shortcuts (`Ctrl+A`, `Escape`).
- **Native OpenXML Microsoft Visio (.vsdx) Export**: Pure vector drawing generation with dynamic connectors and 2-D connection points without Microsoft Visio installation.
- **Native Diagrams.net (Draw.io) Export**: Full layout parity with terminal-anchored port badges.
- **In-App Auto-Updates & Security**: SHA-256 cryptographic checksums, PE header validation (`MZ` magic bytes), silent in-place installation, and manifest auto-generation.
- **188 Automated Tests Passing (100%)**: Comprehensive unit and headless Avalonia UI interaction test suites.

---

## [1.0.0-beta.2] - 2026-11-05

### Added & Modernized (Network Health Reporter UI/UX Parity)
- **Skia Vector Topology Canvas Parity (Req 1)**:
  - Topology canvas styled with `CardBackgroundFillColorDefaultBrush`, top accent role stripes (5px), dual-end port badges, and dynamic link re-routing matching Network Health Reporter.
- **FluentAvalonia Hamburger Navigation (Req 2)**:
  - Modernized sidebar navigation using FluentAvalonia `ui:NavigationView` with `PaneDisplayMode="LeftCompact"` (48px collapsed, 220px expanded).
- **Anchored About & System Section (Req 3)**:
  - Repositioned About & System navigation item firmly into `<ui:NavigationView.FooterMenuItems>` at the drawer bottom.
- **Native FullScreen Handler (Req 4)**:
  - Implemented `F11` key and `Escape` key handlers and canvas toolbar button with dynamic icon (`FullScreen` vs `BackToWindow`) to toggle the diagram workspace in and out of full screen.
- **Excised Legacy Sidebar Card (Req 5)**:
  - Completely removed obsolete floating "Runs offline / Linked Page / By Yash Nalawde" card from the lower-left sidebar.
- **Exclusive Diagnostic Logging Console (Req 6)**:
  - Consolidated application logs exclusively into Card 4 of `AboutView.axaml` with monospace formatting, Clear Logs, Copy Logs, and Open Folder actions; removed status bar log button from canvas.
- **In-App Software Updates Engine (Req 7)**:
  - Full-featured `UpdateService.cs` with SemVer comparison, SHA-256 cryptographic verification of downloaded installer packages, PE header validation (`MZ` magic bytes), silent in-place installation, and expandable changelog history.
- **Inputs Workflow Overhaul (Req 8)**:
  - Initial application launch lands on `InputsView.axaml` for backup archive (.zip/folder), inventory (.xlsx), or live SSH CDP discovery selection.
  - Successful diagram build automatically transitions view to `CanvasView.axaml` and synchronizes sidebar selection.
  - "New Diagram" button on canvas toolbar cleanly returns the user to `InputsView` while resetting selection and project state.
- **Device Tree Toggle Control (Req 9)**:
  - Added show/hide toggle button on canvas toolbar collapsing/expanding the 240px Network Topology sidebar panel (collapsing column width to 0px).
- **Theme System Parity (Req 10)**:
  - Title bar rounded pill toggle (`Highlight` sun / `DarkTheme` moon) wired to `ThemeService.cs` with global dynamic resource propagation across dark, light, and system themes with zero color leaks.
- **High-DPI Application Logo (Req 11)**:
  - Sharp 64x64 vector-rendered application logo (`Assets/app.png`) embedded in About view Card 1.
- **Custom 38px Title Bar (Req 12)**:
  - Custom 38px title bar with OS caption button clearance (142px Windows, 78px macOS), drag/double-click window management, zoom pill, and developer badge.
- **Deduplicated Headings (Req 13)**:
  - Eliminated redundant sub-header beneath the title bar, establishing the custom title bar as the single authoritative window header.
- **Infinite Canvas & NetHealth Interaction Methodology**:
  - Virtual infinite workspace (`Math.Max(4000, ...)` × `Math.Max(3000, ...)`) with auto-expanding boundaries when nodes are moved.
  - Multi-node selection (`SelectedNodeIds`) with synchronized group dragging across all selected nodes.
  - Marquee selection overlay with real-time AABB intersection bounding box selection.
  - Cursor-centered mouse-wheel zoom and middle-click / right-click / Space+drag panning with `SizeAll` cursor.
  - Keyboard shortcuts `Ctrl+A` (Select All) and `Escape` (Clear Selection).
- **Pixel-Perfect Port Badge Alignment & Rotation**:
  - Vertical links display vertical badges rotated +90° reading cleanly from top to bottom.
  - Badges horizontally centered on vertical wire segments and vertically centered on horizontal wire segments with 4px node clearance.
  - Dynamic font measurement snugly wraps badges without blank excess padding.
- **Draw.io Export Terminal Anchoring**:
  - Edge labels exported with `relative="1"` anchored to terminals (`x="-1"` for source, `x="1"` for target) and directional pixel offsets (`offX`, `offY`), preserving exact port placement when nodes are moved in diagrams.net.
  - Synchronized color palette matching canvas: Sky Blue for copper, Gold for fiber, Purple for port-channels, Emerald for APs, Amber for IP phones.
- **Comprehensive E2E Test Suite**:
  - Expanded test coverage to 169 automated tests (107 unit tests in `VisioCreator.Tests` + 62 UI tests in `VisioCreator.UiTests`) with 100% pass rate.
- **Release Packaging**:
  - Standalone single-file win-x64 binary `dist\win-x64\VisioCreator.exe` (52.85 MB).
  - Portable zip distribution `dist\VisioCreator-v1.0.0-beta.2-win-x64-portable.zip` (47.38 MB).
  - Inno Setup Windows installer `dist\VisioCreator_Setup_v1.0.0-beta.2.exe` (47.73 MB).
  - Cryptographic checksums `dist\SHA256SUMS.txt`.

---

## [1.0.0-beta] - 2026-10-25

### Added
- **Avalonia Cross-Platform UI (`VisioCreator.Desktop`)**:
  - Full cross-platform desktop UI targeting .NET 10 on Windows, Linux, and macOS.
  - Interactive topology canvas with zoom, pan, real-time node drag, and auto-rerouting.
  - Integrated evidence inspector, device search, and real-time reconciliation logs.
  - Schema-versioned project save/load (`.json`) with atomic file writes.
- **Headless Command-Line Interface (`VisioCreator.Cli`)**:
  - Direct headless execution from terminal for automated CI/CD pipeline diagramming.
  - Generates `.vsdx` diagrams from inventory workbooks, Cisco backups, and saved project files.
- **Topological & Layout Improvements**:
  - Adopted validated graph engine enhancements: rejection of blank, invalid, or self endpoints.
  - Disambiguation for truncated switch hostnames and domain stripping (`.jsw.in`, `.corp.local`).
  - Campus AP, IP Phone, and Wireless LAN Controller (WLC) role aliases and hierarchy tiers.
  - Dynamic route bypass for intervening nodes and bounded row wrapping for dense access layers.
  - Independent layout snapshot cloning (`CreateSnapshot`) ensuring dragged coordinates accurately translate to Visio exports.
  - Automatic diagram bounding box expansion when nodes are dragged outside initial canvas margins.
- **Visio OpenXML Rendering Enhancements**:
  - Explicit bounding `Geometry` section on companion shape text blocks (hostnames & management IPs) to guarantee crisp text rendering in Visio.
  - Centered alignment and zero vertical padding on PortChannel highlight capsules.
  - Native interactive Visio Dynamic Connectors with right-angle routing.
  - Custom stencil loading from `.vssx` with explicit failure reporting when masters are unusable.
- **Standardized About & System View**:
  - 3-card Fluent layout (App Specifications, Developer Details, Feature Capabilities & Technical Coverage).
  - Subtle TitleBar tag `[By Yash Nalawde]` and sidebar navigation drawer footer with LinkedIn shortcut button.
  - Diagnostic console/log entry emitted on application startup.
  - Persistent file logging to `%APPDATA%\VisioCreator\Logs\visiocreator.log`.
- **Validation Suite**:
  - Comprehensive 103-test suite (93 core unit tests, 10 integration benchmarks, 2 headless Skia UI tests).
  - Cross-platform CI GitHub Actions workflow across Ubuntu, Windows, and macOS.
  - Single-file package script (`scripts/package.ps1`) for self-contained desktop deployment.

---

## [0.9.0] - 2026-10-15

### Added
- **Windows 11 Fluent Application Icon**:
  - Custom vector-designed application icon (`app.ico` multi-res 16-256 and `app.png`).
  - Embedded icon in executable binaries and title bars.
- **Canvas Interaction & Alignment**:
  - Fluid component drag-and-drop with smart magnetic alignment guides.
  - Infinite vector canvas with dynamic view bounds.
  - Granular layer toggles for Access Points, IP Phones, and PortChannels.

---

## [0.8.0] - 2026-10-14

### Added
- **Hierarchical Layout & Live Discovery**:
  - Deterministic BFS graph layout engine placing Core, Distribution, and Access switches in hierarchical rows.
  - Leaf node grouping for Access Points directly below parent switch ports.
  - Live SSH seed switch crawler with recursive CDP/LLDP neighbor traversal.
  - Endpoint identification skipping SSH traversal for IP phones and APs.

---

## [0.7.0] - 2026-10-05

### Added
- **Initial Native Visio OpenXML Exporter**:
  - Direct `.vsdx` package generation using OpenXML SDK without requiring Microsoft Visio installed.
  - Custom stencil mapping (`.vssx`) support with JSON role mappings.
  - ShapeSheet geometry and connector routing.
