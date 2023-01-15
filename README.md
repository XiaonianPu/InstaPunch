# InstaPunch
InstaPunch™ is a Orienteering Event Management software based on PySide6 GUI framework. It consists of **Event Manager** and **Readout Router**.

- Support **SPORTIdent**, **ChinaHealth** orienteering punching system.
- Enable full-life-circle, multi-days event management.
  - Competitor management with club, entry, chip.
  - Course management for each competition day, support IOX-XML 3.0 import and
  - Support special orienteering principle (): Team and Credit competition. Event allow custom principles.
- Distribute and networking: with **Readout Router**, support N (N>0) chip readout endpoints and M (M>0)  result centers.
- Storage and security: Event data stored in Sqlite3 single file database with SQLCipher3 HMAC-512 encryption.
- Competitor import/export via CSV file

Software available in [release page](https://github.com/XiaonianPu/InstaPunch/releases), please contact sserxiaonian@gmail.com for beta test license.

More information in [here](https://xnorienteering.club)
