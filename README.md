# RF Setups and Test Requirements — Master Notes

Task list (Confluence): https://saronic.atlassian-us-gov-mod.net/wiki/spaces/mr/pages/edit-v2/180916001

This is the single notes file for the project. Folder contents are in `FolderIndex.md`. Superseded note files are in `archive\notes_superseded\`; the version of this file from before the cleanup is kept there too.

## 1. Task definitions

**TK1: RF test equipment selection to support FLA AI&T** (original list, kept as written)

- All weather power strip
- RF cables list
- ZNL Vector Network Analyzer
- VNA Cal Kit: https://www.rohde-schwarz.com/us/products/test-and-measurement/vna-accessories/rs-zn-z1xx-network-analyzer-calibration-kits-economy_63493-747623.html
- Transport cases needed: https://a.co/d/0cm9rpiA (transport rack/case for sound industry); https://www.mcmaster.com/9031T17/ (Slope-Top Steel Cart)
- SGS100A: https://www.rohde-schwarz.com/us/products/test-and-measurement/analog-signal-generators/rs-sgs100a-sgma-rf-source_63493-9030.html — **FANS FANS**
- ZZA-KN21: https://www.tequipment.net/Rohde-&-Schwarz/ZZA-KN21/Rack-Mounts/
- Rack Mount Drawer to store accessories: https://www.startech.com/en-us/server-management/3u-rack-mount-drawer

**TK2:** Create RF test setup block diagram, incl. all important details to generate a BOM.

**TK3:** Generate RF test setup BOM based on block diagram.

**TK-4:** Generate functional RF test setup diagram along with a detailed description. Plan and status are in `TK4_Plan.md`.

**TK-6:** Create RF test requirements document for each Marauder RF subsystem and hardware. This will support hardware and subassembly testing during Assembly Integration & Testing phases.

## 2. Working rules

- Ask for specific changes instead of "review everything". Re-reading large PDFs and workbooks uses the most capacity.
- Keep finished items in the files (a dated status bullet in section 4) rather than in the chat.
- Lead feedback (2026-11-18): keep test documents at low detail. IQC uses the lead's per-PN key-parameter list, and SUB and EOL are short checklists.
- Source of truth: 440-001 RF System Diagram Rev 10.0 (top level + .01–.07). The functional diagram is reference only.

## 3. Current files

| What | File |
|---|---|
| Master workbook | `RFSetup\MUSV_RF_Test_Setup_and_Requirements_DRAFT_v0.11.xlsx` |
| Test requirements docs | `TK6 Test Requirements Documents\MUSV-RF-TR-000…007_*_DRAFT_v0.3.docx` |
| Block diagram | `RF test setup block diagram\MUSV_RF_Test_Setup_Block_Diagram_v0.3.drawio` (PDF still v0.2, to re-export) |
| Lead's IQC list (`saronic_pn`, `Key Parameters`) | `rf_marauder_test_req_1.0v.xlsx` |
| Spec sheets (values for the IQC parameters) | `SpecSheets\` (files named `<PN>_*.pdf`) |
| Engineering drawings | `RF test setup block diagram\Eng System Diagrams\` |
| ICD and design docs | `ICD_DOCs\` |
| TK-4 working files | `TK4_Plan.md`, `TK4_Functional_Block_Model.md`, `tools\` |
| Mast power budget | `Mast_Power_Budget.md` |
| Meeting notes (Nov 16) | `meetings\MondayNov16Minutes.md` (minutes), `meetings\1116_CheckIn_Notes_Clean.md` (transcription of the HEIC pages) |

## 4. Status log (oldest first)

**2026-11-18: Lead feedback applied**
- TK6 docs revised to Draft v0.2 (less detail): `TK6 Test Requirements Documents\MUSV-RF-TR-000…007_*_DRAFT_v0.2.docx`
- IQC now per Saronic PN from rf_marauder_test_req_1.0v.xlsx, values from SpecSheets; SUB and EOL cut to short checklists
- New docs: TR-005 5G/LTE, TR-006 VHF/AIS, TR-007 Radar (all 31 PNs on the lead list covered)
- Master: workbook v0.8, tab "TK6 IQC Key Parameters"
- Open: 233-00155 / 233-00286 no datasheet; 242-00266 vs 242-00267; equipment gaps (Open Questions tab)

**2026-11-19: Source of truth resolved (open question #4)**
- Source of truth: 440-001 RF System Diagram Rev 10.0, top level + 440-001.01–.07 ("RF test setup block diagram\Eng System Diagrams"). Top level and sub-assembly sheets agree. Functional diagram is reference only.
- TK6 docs revised to Draft v0.3 (ref des, qty, location and cable IDs from the drawings; bands from RFSC Frequency Plan Rev 1.0)
- Workbook v0.9: Hardware Inventory rebuilt (31 PNs, 78 items, 38 cables); Drawing Discrepancies resolved; Open Questions updated
- Block diagram v0.2 (.drawio + PDF, 7 sheets): Sheet 6 VHF/AIS, Sheet 7 Radar + Cell/LTE added; references updated
- Still open: 'F250' cable type, 233-00165 3-way?, TXR4 J1 load, datasheets for 233-00155 / 233-00286

**2026-11-19: TK1/TK2/TK3 extended to all 7 subsystems**
- Workbook v0.10 (RFSetup): new items E15 radio/AIS comm tester, E16 scope/counter, E17 e-load, E18 Furuno display, E19 higher-power DC supply, E20 SIMs/airtime, E21 reference AIS/VHF; C08–C11 test cables; A15–A19 adapters, serial/NMEA kit, step attenuator, WR-90 adapter
- All diagram tags cross-checked against the BOM (both directions); BOM now 59 lines, priced subtotal unchanged at $73,614
- Open: approve/quote the new gap items; who supplies E18, E20, E21

**2026-11-20: TK-4 started** (details in `TK4_Plan.md`)
- Decisions: system-level test bed functional diagram (2 sheets), Word description doc MUSV-RF-TS-001, separate .drawio, all 7 subsystems at low detail, E15–E21 orange "proposed"
- Steps 1–2 done: `TK4_Functional_Block_Model.md` is ready for review (checkpoint before drawing)

**2026-11-23: Mast power budget**
- `Mast_Power_Budget.md`: per-sub-assembly mast-stage power from ICD Rev 6.0 Table 3, mapped to block diagram v0.2 Sheets 3/4/6/7
- Open: S-band radar is 230 VAC / 736 W (E19 is spec'd as 24 V DC); Starlink 150 W cannot run from E08 PoE+; Cell modem at the PoE+ limit; ICD voltage typos

**2026-11-23: E19 corrected / FLA 120 VAC flagged**
- Workbook v0.11 (RFSetup): E19 (TK1 F24/L24, TK3 F23/K23) now uses ICD Rev 6.0 Table 3. The S-band radar is 230 VAC, 736 W max (RPSU 483 + RPU 253 W), so it is not a DC load. R07 note and Open Question 28: FLA site AC is 120 VAC, so a 230 VAC source (≥ 1 kVA step-up or 240 V circuit) is needed
- Block diagram v0.3 .drawio: E19 box (Sheet 7) and Site AC box (Sheet 1) updated, title blocks set to v0.3. PDF still v0.2 and needs re-exporting from draw.io
- Open: E19 V/A re-size without the radar; TK6 IQC Key Parameters L125 still cites FAR-2228 329 W vs E06

**2026-11-23: Note files simplified**
- One master notes file (this one). Moved to `archive\notes_superseded\`: `RFsetupsAndTestRequirements.txt`, `Develop RF setups and tests requirements.txt`, `RFTestBed.md`, `meetings\MondayNov16MinutesUpdate.md` (identical copy), `meetings\MondayNov16Minutes.txt`, plus a pre-cleanup copy of this file. `1116_CheckIn_Notes_Clean.md` moved into `meetings\`. Nothing deleted.
