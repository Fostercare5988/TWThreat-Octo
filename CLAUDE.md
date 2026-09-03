# Mandatory AI Directives for OctoWoW Addon Development

Before analyzing, refactoring, editing, or committing code in this repository:

1. **Master Authority**:
   Strictly read and follow the master directives in:
   `c:/Users/Fostercare/Documents/System Prompts/OCTOWOW_SYSTEM_PROMPT.md`

2. **Mandatory Client Extension Stack**:
   All addons strictly require and leverage:
   - **ClassicAPI v1.13.3+** (C++ timers, native table.wipe, C_UnitAuras, modern EditBox API)
   - **SuperWoW v2.2+** (Direct GUID targeting TargetUnit(guid), SetMouseoverUnit)
   - **NamPower v4.6.2+** (Zero-latency spell queue, binary combat log packets)
   - **UnitXP SP3 v89+** (Final release: Uncapped 3D Euclidean distances and real HP integers)
   - **DXVK** (Vulkan frame pacing translation layer)
   - Never write 2006 legacy fallbacks, tooltip scans, or manual nil loops.

3. **Mandatory Automated Static Linter Gatekeeper**:
   Before every commit, run the automated auditor:
   `python "c:/Users/Fostercare/Documents/System Prompts/tools/octowow_linter.py" .`
   Every commit MUST pass with 0 issues and 0 warnings.

4. **Strict 100% English Standard (Rule H2)**:
   All code, comments, UI text, and documentation must be 100% English.
   Never preserve or write foreign localization (deDE, frFR, ruRU, zhCN) files or conditionals.

5. **Single Branch Git Standardization**:
   Strictly maintain and push to 1 single branch (main or master). Never create extraneous branches.

6. **Continuous Learning Protocol (Rule H6)**:
   When resolving any new bug or edge-case, immediately record the anti-pattern in OCTOWOW_SYSTEM_PROMPT.md (Part I) and add a test in tools/octowow_linter.py.
