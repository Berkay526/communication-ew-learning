# Phase 08 — PCB & Communication Hardware

Connecting electronics and PCB design to the communication system.

## Hardware Projects

1. STM32 + UART test board
2. RS-485 communication board
3. CAN node board
4. SPI / I²C sensor board
5. RF module carrier
6. Basic impedance-matching network
7. Advanced RF / SDR board

## RF PCB Topics

* 50 Ω transmission lines & impedance-controlled routing
* Ground planes & return current paths
* Decoupling & power integrity
* RF trace geometry
* Connector launches & transitions
* Shielding & EMI / EMC fundamentals
* Matching networks
* LNA / PA / filter / switch blocks
* PCB stackup & 4-layer design

## Tools

KiCad · Altium

## Goal

Understand how **PCB layout and hardware decisions affect signal integrity, RF performance, and communication systems**.

## Sources

**IPC standards**
- [IPC-2221C: Generic Standard on Printed Board Design](https://shop.ipc.org/ipc-2221/ipc-2221-standard-only/Revision-c/english) (2023)
- [IPC-2141A: Design Guide for High-Speed Controlled Impedance Circuit Boards](https://www.electronics.org/TOC/IPC-2141A.pdf) (2004)
- [IPC-2251: Design Guide for the Packaging of High Speed Electronic Circuits](https://shop.ipc.org/ipc-2251/ipc-2251-standard-only/Revision-0/english) (2003)
- [IPC-2252: Design Guide for RF/Microwave Circuit Boards](https://www.electronics.org/TOC/IPC-2252.PDF) (2002, covers 100 MHz–30 GHz)
- [IPC-2152: Current Carrying Capacity](https://shop.ipc.org/ipc-2152/ipc-2152-standard-only/Revision-0/english) (2009)
- [IPC-4101F: Base Materials for Rigid and Multilayer Boards](https://webstore.ansi.org/standards/ipc/ipc4101f2026) (2026)
- [IPC-4103B: Base Materials for High Speed/High Frequency](https://standards.globalspec.com/std/10265180/ipc-4103) (2017)
- [IPC-4761: Protection of Via Structures](https://www.electronics.org/TOC/IPC-4761.pdf) (Type VII = "Filled and Capped" is confirmed)
- [IPC-6012F: Rigid Printed Boards](https://www.electronics.org/news-release/ipc-releases-ipc-6012f-qualification-and-performance-specification-rigid-printed) (2023)
- [IPC-6018D: High Frequency (Microwave) Printed Boards](https://shop.ipc.org/ipc-6018/ipc-6018-standard-only/Revision-d/english)
- IPC-TM-650 [2.5.5.7A (TDR impedance)](https://www.electronics.org/sites/default/files/test_methods_docs/2-5-5-7a.pdf) and [2.5.5.5C (X-band stripline Dk/Df)](https://www.electronics.org/sites/default/files/test_methods_docs/2-5_2-5-5-5.pdf). These test methods are free to download.

**Other standards**
- [IEEE 370-2020: PCB interconnect characterization up to 50 GHz](https://standards.ieee.org/ieee/370/6165/)
- [IEEE 299-2006: shielding enclosure effectiveness](https://standards.ieee.org/ieee/299/493/) (inactive)
- [IEC 61169-15:2021: SMA sectional specification](https://cdn.standards.iteh.ai/samples/101730/41a5144464e04f98bbd9f6f02635cb3d/IEC-61169-15-2021.pdf)
- [IEC 61000-4-2 Ed. 3.0 (2025)](https://webstore.iec.ch/en/publication/68954) and [IEC 61000-4-3 Ed. 4.0 (2020)](https://webstore.iec.ch/en/publication/59849)
- [CISPR 32 Ed. 2.1](https://webstore.iec.ch/en/publication/65836) and [CISPR 25 Ed. 5.0](https://webstore.iec.ch/en/publication/64645)
- [MIL-STD-461G](https://s3vi.ndc.nasa.gov/ssri-kb/static/resources/MIL-STD-461G.pdf) and a [review of 461H](https://incompliancemag.com/mil-std-461h-a-review/)
- [MIL-STD-464D](https://quicksearch.dla.mil/qsDocDetails.aspx?ident_number=35794)
- [MIL-STD-348B (Change 4, 2024)](https://standards.globalspec.com/std/10072654/mil-std-348)
- [ETSI EN 300 220-1](https://www.etsi.org/deliver/etsi_en/300200_300299/30022001/03.01.01_60/en_30022001v030101p.pdf) and [EN 300 220-2 V3.3.1](https://www.etsi.org/deliver/etsi_en/300200_300299/30022002/03.03.01_60/en_30022002v030301p.pdf)

**Datasheet and EDA documentation**
- [Rogers RO4350B datasheet](https://www.rogerscorp.com/-/media/project/rogerscorp/documents/advanced-electronics-solutions/english/data-sheets/ro4000-laminates-ro4003c-and-ro4350b---data-sheet.pdf)
- KiCad 10: [PCB Calculator](https://docs.kicad.org/10.0/en/pcb_calculator/pcb_calculator.html) (confirmed: CPWG, stripline) and [custom DRC rules](https://docs.kicad.org/10.0/en/pcbnew/pcbnew.html)
- Altium: [Via Stitching/Shielding](https://www.altium.com/documentation/altium-designer/pcb/via-stitching-via-shielding) and [controlled-impedance routing](https://www.altium.com/documentation/altium-designer/pcb/high-speed-design/interactively-routing-controlled-impedance)
- Allegro: [Constraint Manager guide](https://resources.pcb.cadence.com/constraint-manager-user-guide/00-introduction-to-constraint-manager). The via-array feature was confirmed only by a Cadence partner, [Parallel Systems](https://www.parallel-systems.co.uk/wp-content/uploads/2020/02/Via_Arrays.pdf).

**Books**
- Pozar, *Microwave Engineering*, 4th ed., Wiley 2012, ISBN 978-0-470-63155-3. A new edition is listed for pre-order for 2027.
- Johnson & Graham, *High-Speed Digital Design*, Prentice Hall 1993 ([author's page](https://sigcon.com/books/bookHSDD.html))
- Bogatin, *Signal and Power Integrity — Simplified*, 3rd ed., Pearson 2017 ([InformIT](https://www.informit.com/store/signal-and-power-integrity-simplified-9780134512204))
- Ott, *Electromagnetic Compatibility Engineering*, Wiley 2009 ([Wiley Online Library](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470508510))
- Simons, *Coplanar Waveguide Circuits, Components, and Systems*, Wiley 2001 ([Wiley Online Library](https://onlinelibrary.wiley.com/doi/book/10.1002/0471224758))
- Gupta, Garg, Bahl, Bhartia, *Microstrip Lines and Slotlines*, 2nd ed., Artech House 1996, ISBN 978-0-89006-766-6
- Bowick, Blyler, Ajluni, *RF Circuit Design*, 2nd ed., Newnes 2007 ([Elsevier](https://shop.elsevier.com/books/rf-circuit-design/bowick/978-0-7506-8518-4))

**Papers**
- Hammerstad & Jensen, "Accurate Models for Microstrip Computer-Aided Design," IEEE MTT-S 1980, [doi:10.1109/MWSYM.1980.1124303](https://ieeexplore.ieee.org/document/1124303/)
- Douville & James, IEEE Trans. MTT vol. 26, 1978, [IEEE Xplore 1129340](https://ieeexplore.ieee.org/document/1129340/)
- Rollett, "Stability and Power-Gain Invariants of Linear Twoports," IRE Trans. CT 1962, [doi:10.1109/TCT.1962.1086854](https://ieeexplore.ieee.org/document/1086854/)
- Groiss et al., IEEE Trans. Magnetics 1996, [doi:10.1109/20.497385](https://ieeexplore.ieee.org/document/497385/)
- Shim & Hubing, "20-H rule modeling and measurements," IEEE EMC 2001, doi:10.1109/ISEMC.2001.950514

**Formula checks.** These were confirmed through secondary sources, not the original paper or book:
- Via inductance: Johnson's own [newsletter](https://sigcon.com/Pubs/news/6_04.htm). He calls the formula "a gross approximation".
- Return-current distribution: [sigcon.com](https://sigcon.com/Pubs/news/3_11.htm)
- Bogatin's 2.3·f·Df·√Dk loss rule: [EDN](https://www.edn.com/loss-in-a-channel-rule-of-thumb-9/)
- The IPC-2141 microstrip formula: [ADI MT-094](https://www.analog.com/media/en/training-seminars/tutorials/mt-094.pdf)
- Douville–James miter: [Wikipedia "Microstrip"](https://en.wikipedia.org/wiki/Microstrip)