EndNote Export Filter for JabRef (Extras)
version 1.1
2004-01-23

Written by Alex Montgomery (ahm@stanford.edu)

********************************************************************************
Overview:
********************************************************************************

The EndNote Export Filter for JabRef allows for most of the default
JabRef fields to be imported into the appropriate EndNote fields.
Three extras are supplied here to be manually installed for better
integration:

1)An improved filter (EndNote Import from JabRef.eni) is provided
since the default EndNote Import filter does not properly parse
authors or editors.

2)Two export styles from EndNote ("BibTeX Export to JabRef*") are also
included that support the same fields.

3)Instructions for modifying the EndNote Reference Types by the user
if the user wishes to have EndNote display the proper field names in
the entry window or to add JabRef-specific fields to new EndNote
entries.

The installation of the extra files provided is detailed below. The file
EndNote.tab is provided for reference purposes only; it contains the
mappings from JabRef fields to EndNote/Refer fields.

See end for changes.

********************************************************************************
Installation 1: EndNote Import from JabRef filter
********************************************************************************

EndNote Import from JabRef.eni:
-------------------------------
This file must be placed in your EndNote Filters directory.

On a Mac OS X system, the default directory is 
/Applications/EndNote 7/Filters.

On a Windows XP system, the default directory is 
C:\Program Files\EndNote\Filters 

Note that for EndNote 8, the directory is called EndNote 8 instead of
EndNote 7 (MacOSX) or EndNote (WinXP)

The default EndNote Import filter is able to import the files from
JabRef, but supports many fewer fields and does not parse authors or
editors correctly.  After installation, you should then open up the
Filter Manager (Edit->Import Filters->Open Filter Manager) and add it
to your Favorites so that it appears directly in the Import dialog.

********************************************************************************
Installation 2: Modifying Reference Types
********************************************************************************

In order to have EndNote display proper field names and to add
JabRef-specific fields to new EndNote entries, follow these steps:

ENDNOTE 8:

RefTypeTable.xml:
-------------------------------
On Windows XP, this file should be placed in 
C:\Documents and Settings\<user>\Application Data\EndNote\

On Mac OS X,
~/Library/Application Support/Endnote/

ENDNOTE 7:

Unfortunately, you can't use this file and must modify Reference Types
by hand.  Open up Preferences and click on Reference Types, then
Modify Reference Types. The following table lists the field names that
must be added to certain reference types for EndNote to support these
fields. For example, the Publisher field for Journal Article is blank
by default; Type in Publisher in this field.

Generic Name 	    	New Field Name	Ref Types
Publisher		Publisher	(Journal Article, Newspaper Article, 
						 Magazine Article)
Section			Section 		(Book Section)
Type of Work		Type of Work 	(Book Section)
Date			Date 		(Book, Book Section, Edited Book, 
					       Thesis, Computer Program)
Number			Number		(Personal Communication)
Custom 1		pdf		(All)
Custom 2		comment		(All)
Custom 3		entrytype	(All)
Custom 4		crossref	(All)
Custom 5		owner		(All)
Custom 6		key		(All)

(All = Journal Article, Book, Book Section, Manuscript, Edited Book,
Magazine Article, Newspaper Article, Conference Proceedings, Thesis,
Report, Personal Communication, Computer Program, Electronic Source)

********************************************************************************
Installation 3: Export to JabRef from EndNote
********************************************************************************

BibTeX Export to JabRef.ens, BibTeX Export to JabRef2.ens
-------------------------------

These files are required only if you wish to export EndNote entries to
JabRef. They must be placed in your EndNote Styles directory. 

On a Mac OS X system, the default directory is 
/Applications/EndNote 7/Styles. 

On a Windows XP system, the default directory is 
C:\Program Files\EndNote\Styles

You may then want to open up the Style Manager (Edit->Output
Styles->Open Style Manager) and add it to your Favorites.

To re-export to JabRef, two EndNote Styles are provided. Select a
style (see "Notes" for the problems with each), then select
File->Export. The exported text file is a BibTeX file ready to be read
by JabRef.

Note that if you use EndNote as your primary manager, this export file
will do a better job than the default BibTeX Export. Improvements in
specific mappings are noted below. General improvements include:

All: 	Maps Custom 1-6 fields to pdf/comment/entrytype/crossref/owner/key
	Includes URL
	Includes EndNoteRefType
	Includes ShortTitle
	Includes ISBN/ISSN where appropriate

Mapping Endnote -> BibTeX (improvement over default)
----------------------------------------------------
	Generic -> misc (correctly maps Publisher->Howpublished)
	Journal Article -> article
	Book -> book (maps Editor,Number of Volumes)
	Book Section -> incollection (maps Section,Date,Type of Work)
	Conference Proceedings -> inproceedings (maps Organization,Edition,Date)
	Report -> techreport (maps City)
	Thesis -> phdthesis (maps City,Date)
	Magazine Article -> article
	Newspaper Article -> article (new)
	Edited Book -> book (maps Number of Volumes)
	Electronic Source -> misc (new)
	Manuscript -> unpublished (new)
	Computer Program -> manual (new)
	Personal Communication -> booklet (new)

Other EndNote Reference Types will be mapped to misc.

********************************************************************************
Notes:
********************************************************************************

The export format implemented is the EndNote Import format, an
extension of the Refer format. It does NOT export in the proprietary
.enl format.

Only two JabRef fields are unsupported due to a lack of Custom fields
in EndNote: doi and citeseerurl. Enterprising users should be able to
modify the enclosed files in order to swap out two other fields
(e.g. pdf and owner) instead. Note that EndNote 8 has additional
fields that could be ideal for doi and citeseerurl (part of the reason
why these are excluded here). In particular, Electronic Resource
Number (DOI) and Link to PDF. The latter is actually a URL field, not
a relative field like the pdf field in JabRef, so it would actually be
better for citeseerurl than pdf. Unfortunately, ISI ResearchSoft has
established no new extension of the Refer standard to include these
fields, so any immediate solution would be likely to break later.

This has been tested on Mac OS X 10.3.7 and Windows XP SP2 using
JabRef 1.7 and EndNote 7. It should work on EndNote 8 on either
platform.

BibTeX Export to JabRef munges together some BibTeX types (e.g. if you
exported, then reimported, your .bib file, it would be mapped
inbook/incollection -> Book Section -> incollection). Use BibTeX
Export to JabRef2 instead if you need better mapping - but only if you
are using field Custom 3 (entrytype) to store the BibTeX entrytypes.

BibTeX Export to JabRef2 is ONLY for use if you are re-exporting a
file that was imported from JabRef. This is because it uses Custom 3
(entrytype) to store and output the entrytype rather than guessing
from the EndNote reference type. If this field isn't filled in, it
will export bad BibTeX code. You have been warned.

********************************************************************************
Special note on corporate authors:
********************************************************************************

Endnote doesn't properly output corporate authors. To have Endnote
output corporate authors for use in BibTeX, enter them as
{Central Intelligence Agency},

However, other EndNote styles will then include the brackets.

********************************************************************************
Changes:
********************************************************************************

1.1:	2005-01-23
	RefTypeTable.xml:
		Added so that Endnote 8 users don't have to modify their 
ReferenceTypes.
	BibTeX Export to JabRef:
		Bugfix: If Label was missing, entrytype line was deleted.
		Bugfix: Book Section mapped to inbook, now incollection.
		EndNoteRefType added to all output styles.
		Added ISBN/ISSN to export where appropriate.
		Output styles added: 
			Magazine Article -> article
			Newspaper Article -> article
			Edited Book -> book
			Electronic Source -> misc
			Manuscript -> unpublished
			Computer Program -> manual
	BibTeX Export to JabRef2:
		Same modifications as above. 
		Bugfix: File renamed to eliminate problems with Windows XP.
	EndNote.*.layout/Endnote Import from JabRef:
		Bugfix: Corporate authors were not properly formatted.
	         Bugfix: Editors were not properly formatted.
		Bugfix:	EndNote.techreport.layout did not export report number
		Updated to use EndNoteRefType field if it exists
		Updated to include ISBN/ISSN if it exists
		Layouts/New mappings added:
			unpublished -> Manuscript
			manual -> Computer Program
			booklet -> Personal Communication
				(\lastchecked field now mapped to Number field)
1.0: Initial version, 2004-12-02
