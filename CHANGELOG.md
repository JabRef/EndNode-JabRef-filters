# Changelog

## 1.1 - 2005-01-23

- RefTypeTable.xml:
  - Added so that Endnote 8 users don't have to modify their ReferenceTypes.
- BibTeX Export to JabRef:
  - Bugfix: If Label was missing, entrytype line was deleted.
  - Bugfix: Book Section mapped to inbook, now incollection.
  - EndNoteRefType added to all output styles.
  - Added ISBN/ISSN to export where appropriate.
  - Output styles added:
    - Magazine Article -> article
    - Newspaper Article -> article
    - Edited Book -> book
    - Electronic Source -> misc
    - Manuscript -> unpublished
    - Computer Program -> manual
- BibTeX Export to JabRef2:
  - Same modifications as above.
  - Bugfix: File renamed to eliminate problems with Windows XP.
- EndNote.*.layout/Endnote Import from JabRef:
  - Bugfix: Corporate authors were not properly formatted.
  -  Bugfix: Editors were not properly formatted.
  - Bugfix:	EndNote.techreport.layout did not export report number
  - Updated to use EndNoteRefType field if it exists
  - Updated to include ISBN/ISSN if it exists
  - Layouts/New mappings added:
    - unpublished -> Manuscript
    - manual -> Computer Program
    - booklet -> Personal Communication
      (\lastchecked field now mapped to Number field)

## 1.0 - 2004-12-02

Initial version
