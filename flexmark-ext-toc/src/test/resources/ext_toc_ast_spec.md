---
title: Toc Extension Spec
author: Vladimir Schneider
version: 0.9.0
date: '2016-06-30'
license: '[CC-BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/)'
...

---

## Toc

Converts `[TOC style]` text to TocBlock nodes.

1. `style` consists of space separated list of options:

   * `levels=levelList` where level list is a comma separated list of levels or ranges. Default
     is to include heading levels 2 and 3. Examples:
     * `levels=4` include levels 2,3 and 4
     * `levels=2-4` include levels 2,3 and 4. same as `levels=4`
     * `levels=2-4,5` include levels 2,3,4 and 5
     * `levels=1,3` include levels 1 and 3

   * `html` generate HTML version of the TOC

   * `markdown` generate Markdown version of the TOC

   * `text` to only include the text of the heading

   * `formatted` to include text and inline formatting

   * `hierarchy` to render as hierarchical list in order of appearance in the document

   * `flat` to render as a flat list in order of appearance in the document

   * `reversed` to render as a flat list in order of appearance in the document

   * `sort-up` to render as a flat list sorted alphabetically by heading text only, no inlines

   * `sort-down` to render as a flat list sorted reversed alphabetically by heading text only,
     no inlines

   * `bullet` to use a bullet list for the TOC items

   * `numbered` to use a numbered list for TOC items

2. `"Title"` specifies the text for the table of contents heading. If omitted or blank then no
   heading will be generated for the table of contents. `#` prefix in the title will specify the
   header level to use for the heading above the table of contents listing. If no `#` prefix is

no spaces between brackets

```````````````````````````````` example Toc: 1
[ TOC] 

[ TOC ] 

[TOC ]
.
<p>[ TOC]</p>
<p>[ TOC ]</p>
<p>[TOC ]</p>
.
Document[0, 25]
  Paragraph[0, 8] isTrailingBlankLine
    LinkRef[0, 6] referenceOpen:[0, 1, "["] reference:[2, 5, "TOC"] referenceClose:[5, 6, "]"]
      Text[2, 5] chars:[2, 5, "TOC"]
  Paragraph[9, 18] isTrailingBlankLine
    LinkRef[9, 16] referenceOpen:[9, 10, "["] reference:[11, 14, "TOC"] referenceClose:[15, 16, "]"]
      Text[11, 14] chars:[11, 14, "TOC"]
  Paragraph[19, 25]
    LinkRef[19, 25] referenceOpen:[19, 20, "["] reference:[20, 23, "TOC"] referenceClose:[24, 25, "]"]
      Text[20, 23] chars:[20, 23, "TOC"]
````````````````````````````````


Invalid level

```````````````````````````````` example Toc: 2
[TOC levels=0] 

[TOC levels=7] 

[TOC levels=8] 

[TOC levels=9] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**
## Heading 1.2
## Heading 1.3
# Heading 2
### Heading 2.0.1
### Heading 2.0.2
.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h2 id="heading-12">Heading 1.2</h2>
<h2 id="heading-13">Heading 1.3</h2>
<h1 id="heading-2">Heading 2</h1>
<h3 id="heading-201">Heading 2.0.1</h3>
<h3 id="heading-202">Heading 2.0.2</h3>
.
Document[0, 260]
  TocBlock[0, 16] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 13] closingMarker:[13, 14]
  TocBlock[17, 33] openingMarker:[17, 18] tocKeyword:[18, 21] style:[22, 30] closingMarker:[30, 31]
  TocBlock[34, 50] openingMarker:[34, 35] tocKeyword:[35, 38] style:[39, 47] closingMarker:[47, 48]
  TocBlock[51, 67] openingMarker:[51, 52] tocKeyword:[52, 55] style:[56, 64] closingMarker:[64, 65]
  Heading[68, 93] textOpen:[68, 69, "#"] text:[70, 93, "Heading **some bold** 1"]
    Text[70, 78] chars:[70, 78, "Heading "]
    StrongEmphasis[78, 91] textOpen:[78, 80, "**"] text:[80, 89, "some bold"] textClose:[89, 91, "**"]
      Text[80, 89] chars:[80, 89, "some bold"]
    Text[91, 93] chars:[91, 93, " 1"]
  Heading[94, 122] textOpen:[94, 96, "##"] text:[97, 122, "Heading 1.1 _some italic_"]
    Text[97, 109] chars:[97, 109, "Headi …  1.1 "]
    Emphasis[109, 122] textOpen:[109, 110, "_"] text:[110, 121, "some italic"] textClose:[121, 122, "_"]
      Text[110, 121] chars:[110, 121, "some  … talic"]
  Heading[123, 140] textOpen:[123, 126, "###"] text:[127, 140, "Heading 1.1.1"]
    Text[127, 140] chars:[127, 140, "Headi … 1.1.1"]
  Heading[141, 182] textOpen:[141, 144, "###"] text:[145, 182, "Heading 1.1.2  **_some bold italic_**"]
    Text[145, 160] chars:[145, 160, "Headi … 1.2  "]
    StrongEmphasis[160, 182] textOpen:[160, 162, "**"] text:[162, 180, "_some bold italic_"] textClose:[180, 182, "**"]
      Emphasis[162, 180] textOpen:[162, 163, "_"] text:[163, 179, "some bold italic"] textClose:[179, 180, "_"]
        Text[163, 179] chars:[163, 179, "some  … talic"]
  Heading[183, 197] textOpen:[183, 185, "##"] text:[186, 197, "Heading 1.2"]
    Text[186, 197] chars:[186, 197, "Headi … g 1.2"]
  Heading[198, 212] textOpen:[198, 200, "##"] text:[201, 212, "Heading 1.3"]
    Text[201, 212] chars:[201, 212, "Headi … g 1.3"]
  Heading[213, 224] textOpen:[213, 214, "#"] text:[215, 224, "Heading 2"]
    Text[215, 224] chars:[215, 224, "Heading 2"]
  Heading[225, 242] textOpen:[225, 228, "###"] text:[229, 242, "Heading 2.0.1"]
    Text[229, 242] chars:[229, 242, "Headi … 2.0.1"]
  Heading[243, 260] textOpen:[243, 246, "###"] text:[247, 260, "Heading 2.0.2"]
    Text[247, 260] chars:[247, 260, "Headi … 2.0.2"]
````````````````````````````````


Default case sensitive

```````````````````````````````` example Toc: 3
[toc] 

# Heading **some bold** 1
## Heading 1.1 _some italic_

.
<p>[toc]</p>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
.
Document[0, 64]
  Paragraph[0, 7] isTrailingBlankLine
    LinkRef[0, 5] referenceOpen:[0, 1, "["] reference:[1, 4, "toc"] referenceClose:[4, 5, "]"]
      Text[1, 4] chars:[1, 4, "toc"]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
````````````````````````````````


case insensitive

```````````````````````````````` example(Toc: 4) options(not-case-sensitive)
[toc] 

# Heading **some bold** 1
## Heading 1.1 _some italic_

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a></li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
.
Document[0, 64]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
````````````````````````````````


```````````````````````````````` example Toc: 5
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**
## Heading 1.2
## Heading 1.3
# Heading 2
### Heading 2.0.1
### Heading 2.0.2

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h2 id="heading-12">Heading 1.2</h2>
<h2 id="heading-13">Heading 1.3</h2>
<h1 id="heading-2">Heading 2</h1>
<h3 id="heading-201">Heading 2.0.1</h3>
<h3 id="heading-202">Heading 2.0.2</h3>
.
Document[0, 202]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
  Heading[81, 122] textOpen:[81, 84, "###"] text:[85, 122, "Heading 1.1.2  **_some bold italic_**"]
    Text[85, 100] chars:[85, 100, "Headi … 1.2  "]
    StrongEmphasis[100, 122] textOpen:[100, 102, "**"] text:[102, 120, "_some bold italic_"] textClose:[120, 122, "**"]
      Emphasis[102, 120] textOpen:[102, 103, "_"] text:[103, 119, "some bold italic"] textClose:[119, 120, "_"]
        Text[103, 119] chars:[103, 119, "some  … talic"]
  Heading[123, 137] textOpen:[123, 125, "##"] text:[126, 137, "Heading 1.2"]
    Text[126, 137] chars:[126, 137, "Headi … g 1.2"]
  Heading[138, 152] textOpen:[138, 140, "##"] text:[141, 152, "Heading 1.3"]
    Text[141, 152] chars:[141, 152, "Headi … g 1.3"]
  Heading[153, 164] textOpen:[153, 154, "#"] text:[155, 164, "Heading 2"]
    Text[155, 164] chars:[155, 164, "Heading 2"]
  Heading[165, 182] textOpen:[165, 168, "###"] text:[169, 182, "Heading 2.0.1"]
    Text[169, 182] chars:[169, 182, "Headi … 2.0.1"]
  Heading[183, 200] textOpen:[183, 186, "###"] text:[187, 200, "Heading 2.0.2"]
    Text[187, 200] chars:[187, 200, "Headi … 2.0.2"]
````````````````````````````````


Default rendering with emphasis

```````````````````````````````` example Toc: 6
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**
.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 122]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
  Heading[81, 122] textOpen:[81, 84, "###"] text:[85, 122, "Heading 1.1.2  **_some bold italic_**"]
    Text[85, 100] chars:[85, 100, "Headi … 1.2  "]
    StrongEmphasis[100, 122] textOpen:[100, 102, "**"] text:[102, 120, "_some bold italic_"] textClose:[120, 122, "**"]
      Emphasis[102, 120] textOpen:[102, 103, "_"] text:[103, 119, "some bold italic"] textClose:[119, 120, "_"]
        Text[103, 119] chars:[103, 119, "some  … talic"]
````````````````````````````````


Set levels rendering

```````````````````````````````` example Toc: 7
[TOC levels=1] 

---

[TOC levels=2] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**
## Heading 1.2
## Heading 1.3
# Heading 2
### Heading 2.0.1
### Heading 2.0.2

.
<ul>
  <li><a href="#heading-some-bold-1">Heading <strong>some bold</strong> 1</a></li>
  <li><a href="#heading-2">Heading 2</a></li>
</ul>
<hr />
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a></li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a></li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h2 id="heading-12">Heading 1.2</h2>
<h2 id="heading-13">Heading 1.3</h2>
<h1 id="heading-2">Heading 2</h1>
<h3 id="heading-201">Heading 2.0.1</h3>
<h3 id="heading-202">Heading 2.0.2</h3>
.
Document[0, 233]
  TocBlock[0, 16] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 13] closingMarker:[13, 14]
  ThematicBreak[17, 20]
  TocBlock[22, 38] openingMarker:[22, 23] tocKeyword:[23, 26] style:[27, 35] closingMarker:[35, 36]
  Heading[39, 64] textOpen:[39, 40, "#"] text:[41, 64, "Heading **some bold** 1"]
    Text[41, 49] chars:[41, 49, "Heading "]
    StrongEmphasis[49, 62] textOpen:[49, 51, "**"] text:[51, 60, "some bold"] textClose:[60, 62, "**"]
      Text[51, 60] chars:[51, 60, "some bold"]
    Text[62, 64] chars:[62, 64, " 1"]
  Heading[65, 93] textOpen:[65, 67, "##"] text:[68, 93, "Heading 1.1 _some italic_"]
    Text[68, 80] chars:[68, 80, "Headi …  1.1 "]
    Emphasis[80, 93] textOpen:[80, 81, "_"] text:[81, 92, "some italic"] textClose:[92, 93, "_"]
      Text[81, 92] chars:[81, 92, "some  … talic"]
  Heading[94, 111] textOpen:[94, 97, "###"] text:[98, 111, "Heading 1.1.1"]
    Text[98, 111] chars:[98, 111, "Headi … 1.1.1"]
  Heading[112, 153] textOpen:[112, 115, "###"] text:[116, 153, "Heading 1.1.2  **_some bold italic_**"]
    Text[116, 131] chars:[116, 131, "Headi … 1.2  "]
    StrongEmphasis[131, 153] textOpen:[131, 133, "**"] text:[133, 151, "_some bold italic_"] textClose:[151, 153, "**"]
      Emphasis[133, 151] textOpen:[133, 134, "_"] text:[134, 150, "some bold italic"] textClose:[150, 151, "_"]
        Text[134, 150] chars:[134, 150, "some  … talic"]
  Heading[154, 168] textOpen:[154, 156, "##"] text:[157, 168, "Heading 1.2"]
    Text[157, 168] chars:[157, 168, "Headi … g 1.2"]
  Heading[169, 183] textOpen:[169, 171, "##"] text:[172, 183, "Heading 1.3"]
    Text[172, 183] chars:[172, 183, "Headi … g 1.3"]
  Heading[184, 195] textOpen:[184, 185, "#"] text:[186, 195, "Heading 2"]
    Text[186, 195] chars:[186, 195, "Heading 2"]
  Heading[196, 213] textOpen:[196, 199, "###"] text:[200, 213, "Heading 2.0.1"]
    Text[200, 213] chars:[200, 213, "Headi … 2.0.1"]
  Heading[214, 231] textOpen:[214, 217, "###"] text:[218, 231, "Heading 2.0.2"]
    Text[218, 231] chars:[218, 231, "Headi … 2.0.2"]
````````````````````````````````


Invalid levels take default

```````````````````````````````` example Toc: 8
[TOC levels=0] 

[TOC levels=7] 

[TOC levels=8] 

[TOC levels=9] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**
## Heading 1.2
## Heading 1.3
# Heading 2
### Heading 2.0.1
### Heading 2.0.2
.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
  <li><a href="#heading-12">Heading 1.2</a></li>
  <li><a href="#heading-13">Heading 1.3</a>
    <ul>
      <li><a href="#heading-201">Heading 2.0.1</a></li>
      <li><a href="#heading-202">Heading 2.0.2</a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h2 id="heading-12">Heading 1.2</h2>
<h2 id="heading-13">Heading 1.3</h2>
<h1 id="heading-2">Heading 2</h1>
<h3 id="heading-201">Heading 2.0.1</h3>
<h3 id="heading-202">Heading 2.0.2</h3>
.
Document[0, 260]
  TocBlock[0, 16] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 13] closingMarker:[13, 14]
  TocBlock[17, 33] openingMarker:[17, 18] tocKeyword:[18, 21] style:[22, 30] closingMarker:[30, 31]
  TocBlock[34, 50] openingMarker:[34, 35] tocKeyword:[35, 38] style:[39, 47] closingMarker:[47, 48]
  TocBlock[51, 67] openingMarker:[51, 52] tocKeyword:[52, 55] style:[56, 64] closingMarker:[64, 65]
  Heading[68, 93] textOpen:[68, 69, "#"] text:[70, 93, "Heading **some bold** 1"]
    Text[70, 78] chars:[70, 78, "Heading "]
    StrongEmphasis[78, 91] textOpen:[78, 80, "**"] text:[80, 89, "some bold"] textClose:[89, 91, "**"]
      Text[80, 89] chars:[80, 89, "some bold"]
    Text[91, 93] chars:[91, 93, " 1"]
  Heading[94, 122] textOpen:[94, 96, "##"] text:[97, 122, "Heading 1.1 _some italic_"]
    Text[97, 109] chars:[97, 109, "Headi …  1.1 "]
    Emphasis[109, 122] textOpen:[109, 110, "_"] text:[110, 121, "some italic"] textClose:[121, 122, "_"]
      Text[110, 121] chars:[110, 121, "some  … talic"]
  Heading[123, 140] textOpen:[123, 126, "###"] text:[127, 140, "Heading 1.1.1"]
    Text[127, 140] chars:[127, 140, "Headi … 1.1.1"]
  Heading[141, 182] textOpen:[141, 144, "###"] text:[145, 182, "Heading 1.1.2  **_some bold italic_**"]
    Text[145, 160] chars:[145, 160, "Headi … 1.2  "]
    StrongEmphasis[160, 182] textOpen:[160, 162, "**"] text:[162, 180, "_some bold italic_"] textClose:[180, 182, "**"]
      Emphasis[162, 180] textOpen:[162, 163, "_"] text:[163, 179, "some bold italic"] textClose:[179, 180, "_"]
        Text[163, 179] chars:[163, 179, "some  … talic"]
  Heading[183, 197] textOpen:[183, 185, "##"] text:[186, 197, "Heading 1.2"]
    Text[186, 197] chars:[186, 197, "Headi … g 1.2"]
  Heading[198, 212] textOpen:[198, 200, "##"] text:[201, 212, "Heading 1.3"]
    Text[201, 212] chars:[201, 212, "Headi … g 1.3"]
  Heading[213, 224] textOpen:[213, 214, "#"] text:[215, 224, "Heading 2"]
    Text[215, 224] chars:[215, 224, "Heading 2"]
  Heading[225, 242] textOpen:[225, 228, "###"] text:[229, 242, "Heading 2.0.1"]
    Text[229, 242] chars:[229, 242, "Headi … 2.0.1"]
  Heading[243, 260] textOpen:[243, 246, "###"] text:[247, 260, "Heading 2.0.2"]
    Text[247, 260] chars:[247, 260, "Headi … 2.0.2"]
````````````````````````````````


Use title

```````````````````````````````` example(Toc: 9) options(title)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
.
<div>
  <h1>Table of Contents</h1>
  <ul>
    <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
      <ul>
        <li><a href="#heading-111">Heading 1.1.1</a></li>
      </ul>
    </li>
  </ul>
</div>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 80]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
````````````````````````````````


Use title, div class

```````````````````````````````` example(Toc: 10) options(title, div-class)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
.
<div class="content-class">
  <h1>Table of Contents</h1>
  <ul>
    <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
      <ul>
        <li><a href="#heading-111">Heading 1.1.1</a></li>
      </ul>
    </li>
  </ul>
</div>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 80]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
````````````````````````````````


Use title, div class, list Class

```````````````````````````````` example(Toc: 11) options(title, div-class, list-class)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
.
<div class="content-class">
  <h1>Table of Contents</h1>
  <ul class="list-class">
    <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
      <ul>
        <li><a href="#heading-111">Heading 1.1.1</a></li>
      </ul>
    </li>
  </ul>
</div>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 80]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
````````````````````````````````


Use list Class

```````````````````````````````` example(Toc: 12) options(list-class)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
.
<ul class="list-class">
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 80]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
````````````````````````````````


Text only rendering

```````````````````````````````` example(Toc: 13) options(text-only)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 some italic</a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  some bold italic</a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
  Heading[81, 122] textOpen:[81, 84, "###"] text:[85, 122, "Heading 1.1.2  **_some bold italic_**"]
    Text[85, 100] chars:[85, 100, "Headi … 1.2  "]
    StrongEmphasis[100, 122] textOpen:[100, 102, "**"] text:[102, 120, "_some bold italic_"] textClose:[120, 122, "**"]
      Emphasis[102, 120] textOpen:[102, 103, "_"] text:[103, 119, "some bold italic"] textClose:[119, 120, "_"]
        Text[103, 119] chars:[103, 119, "some  … talic"]
````````````````````````````````


Text only style

```````````````````````````````` example Toc: 14
[TOC text] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 some italic</a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  some bold italic</a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 129]
  TocBlock[0, 12] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 9] closingMarker:[9, 10]
  Heading[13, 38] textOpen:[13, 14, "#"] text:[15, 38, "Heading **some bold** 1"]
    Text[15, 23] chars:[15, 23, "Heading "]
    StrongEmphasis[23, 36] textOpen:[23, 25, "**"] text:[25, 34, "some bold"] textClose:[34, 36, "**"]
      Text[25, 34] chars:[25, 34, "some bold"]
    Text[36, 38] chars:[36, 38, " 1"]
  Heading[39, 67] textOpen:[39, 41, "##"] text:[42, 67, "Heading 1.1 _some italic_"]
    Text[42, 54] chars:[42, 54, "Headi …  1.1 "]
    Emphasis[54, 67] textOpen:[54, 55, "_"] text:[55, 66, "some italic"] textClose:[66, 67, "_"]
      Text[55, 66] chars:[55, 66, "some  … talic"]
  Heading[68, 85] textOpen:[68, 71, "###"] text:[72, 85, "Heading 1.1.1"]
    Text[72, 85] chars:[72, 85, "Headi … 1.1.1"]
  Heading[86, 127] textOpen:[86, 89, "###"] text:[90, 127, "Heading 1.1.2  **_some bold italic_**"]
    Text[90, 105] chars:[90, 105, "Headi … 1.2  "]
    StrongEmphasis[105, 127] textOpen:[105, 107, "**"] text:[107, 125, "_some bold italic_"] textClose:[125, 127, "**"]
      Emphasis[107, 125] textOpen:[107, 108, "_"] text:[108, 124, "some bold italic"] textClose:[124, 125, "_"]
        Text[108, 124] chars:[108, 124, "some  … talic"]
````````````````````````````````


Text and inlines style

```````````````````````````````` example(Toc: 15) options(text-only)
[TOC format] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 131]
  TocBlock[0, 14] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 11] closingMarker:[11, 12]
  Heading[15, 40] textOpen:[15, 16, "#"] text:[17, 40, "Heading **some bold** 1"]
    Text[17, 25] chars:[17, 25, "Heading "]
    StrongEmphasis[25, 38] textOpen:[25, 27, "**"] text:[27, 36, "some bold"] textClose:[36, 38, "**"]
      Text[27, 36] chars:[27, 36, "some bold"]
    Text[38, 40] chars:[38, 40, " 1"]
  Heading[41, 69] textOpen:[41, 43, "##"] text:[44, 69, "Heading 1.1 _some italic_"]
    Text[44, 56] chars:[44, 56, "Headi …  1.1 "]
    Emphasis[56, 69] textOpen:[56, 57, "_"] text:[57, 68, "some italic"] textClose:[68, 69, "_"]
      Text[57, 68] chars:[57, 68, "some  … talic"]
  Heading[70, 87] textOpen:[70, 73, "###"] text:[74, 87, "Heading 1.1.1"]
    Text[74, 87] chars:[74, 87, "Headi … 1.1.1"]
  Heading[88, 129] textOpen:[88, 91, "###"] text:[92, 129, "Heading 1.1.2  **_some bold italic_**"]
    Text[92, 107] chars:[92, 107, "Headi … 1.2  "]
    StrongEmphasis[107, 129] textOpen:[107, 109, "**"] text:[109, 127, "_some bold italic_"] textClose:[127, 129, "**"]
      Emphasis[109, 127] textOpen:[109, 110, "_"] text:[110, 126, "some bold italic"] textClose:[126, 127, "_"]
        Text[110, 126] chars:[110, 126, "some  … talic"]
````````````````````````````````


Text only, flat

```````````````````````````````` example(Toc: 16) options(text-only, flat)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 some italic</a></li>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  some bold italic</a></li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
  Heading[81, 122] textOpen:[81, 84, "###"] text:[85, 122, "Heading 1.1.2  **_some bold italic_**"]
    Text[85, 100] chars:[85, 100, "Headi … 1.2  "]
    StrongEmphasis[100, 122] textOpen:[100, 102, "**"] text:[102, 120, "_some bold italic_"] textClose:[120, 122, "**"]
      Emphasis[102, 120] textOpen:[102, 103, "_"] text:[103, 119, "some bold italic"] textClose:[119, 120, "_"]
        Text[103, 119] chars:[103, 119, "some  … talic"]
````````````````````````````````


Text and inlines, flat

```````````````````````````````` example(Toc: 17) options(flat)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a></li>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 80] textOpen:[63, 66, "###"] text:[67, 80, "Heading 1.1.1"]
    Text[67, 80] chars:[67, 80, "Headi … 1.1.1"]
  Heading[81, 122] textOpen:[81, 84, "###"] text:[85, 122, "Heading 1.1.2  **_some bold italic_**"]
    Text[85, 100] chars:[85, 100, "Headi … 1.2  "]
    StrongEmphasis[100, 122] textOpen:[100, 102, "**"] text:[102, 120, "_some bold italic_"] textClose:[120, 122, "**"]
      Emphasis[102, 120] textOpen:[102, 103, "_"] text:[103, 119, "some bold italic"] textClose:[119, 120, "_"]
        Text[103, 119] chars:[103, 119, "some  … talic"]
````````````````````````````````


Text only, flat reversed

```````````````````````````````` example(Toc: 18) options(text-only, flat-reversed)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.2  **_some bold italic_**
### Heading 1.1.1

.
<ul>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  some bold italic</a></li>
  <li><a href="#heading-11-some-italic">Heading 1.1 some italic</a></li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 104] textOpen:[63, 66, "###"] text:[67, 104, "Heading 1.1.2  **_some bold italic_**"]
    Text[67, 82] chars:[67, 82, "Headi … 1.2  "]
    StrongEmphasis[82, 104] textOpen:[82, 84, "**"] text:[84, 102, "_some bold italic_"] textClose:[102, 104, "**"]
      Emphasis[84, 102] textOpen:[84, 85, "_"] text:[85, 101, "some bold italic"] textClose:[101, 102, "_"]
        Text[85, 101] chars:[85, 101, "some  … talic"]
  Heading[105, 122] textOpen:[105, 108, "###"] text:[109, 122, "Heading 1.1.1"]
    Text[109, 122] chars:[109, 122, "Headi … 1.1.1"]
````````````````````````````````


Text and inlines, flat

```````````````````````````````` example(Toc: 19) options(flat-reversed)
[TOC] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.2  **_some bold italic_**
### Heading 1.1.1

.
<ul>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a></li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 33] textOpen:[8, 9, "#"] text:[10, 33, "Heading **some bold** 1"]
    Text[10, 18] chars:[10, 18, "Heading "]
    StrongEmphasis[18, 31] textOpen:[18, 20, "**"] text:[20, 29, "some bold"] textClose:[29, 31, "**"]
      Text[20, 29] chars:[20, 29, "some bold"]
    Text[31, 33] chars:[31, 33, " 1"]
  Heading[34, 62] textOpen:[34, 36, "##"] text:[37, 62, "Heading 1.1 _some italic_"]
    Text[37, 49] chars:[37, 49, "Headi …  1.1 "]
    Emphasis[49, 62] textOpen:[49, 50, "_"] text:[50, 61, "some italic"] textClose:[61, 62, "_"]
      Text[50, 61] chars:[50, 61, "some  … talic"]
  Heading[63, 104] textOpen:[63, 66, "###"] text:[67, 104, "Heading 1.1.2  **_some bold italic_**"]
    Text[67, 82] chars:[67, 82, "Headi … 1.2  "]
    StrongEmphasis[82, 104] textOpen:[82, 84, "**"] text:[84, 102, "_some bold italic_"] textClose:[102, 104, "**"]
      Emphasis[84, 102] textOpen:[84, 85, "_"] text:[85, 101, "some bold italic"] textClose:[101, 102, "_"]
        Text[85, 101] chars:[85, 101, "some  … talic"]
  Heading[105, 122] textOpen:[105, 108, "###"] text:[109, 122, "Heading 1.1.1"]
    Text[109, 122] chars:[109, 122, "Headi … 1.1.1"]
````````````````````````````````


Text and inlines, hierarchy

```````````````````````````````` example(Toc: 20) options(sorted)
[TOC hierarchy] 

# Heading **some bold** 1
## Heading 1.1 _some italic_
### Heading 1.1.1
### Heading 1.1.2  **_some bold italic_**

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a>
    <ul>
      <li><a href="#heading-111">Heading 1.1.1</a></li>
      <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
    </ul>
  </li>
</ul>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
.
Document[0, 134]
  TocBlock[0, 17] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 14] closingMarker:[14, 15]
  Heading[18, 43] textOpen:[18, 19, "#"] text:[20, 43, "Heading **some bold** 1"]
    Text[20, 28] chars:[20, 28, "Heading "]
    StrongEmphasis[28, 41] textOpen:[28, 30, "**"] text:[30, 39, "some bold"] textClose:[39, 41, "**"]
      Text[30, 39] chars:[30, 39, "some bold"]
    Text[41, 43] chars:[41, 43, " 1"]
  Heading[44, 72] textOpen:[44, 46, "##"] text:[47, 72, "Heading 1.1 _some italic_"]
    Text[47, 59] chars:[47, 59, "Headi …  1.1 "]
    Emphasis[59, 72] textOpen:[59, 60, "_"] text:[60, 71, "some italic"] textClose:[71, 72, "_"]
      Text[60, 71] chars:[60, 71, "some  … talic"]
  Heading[73, 90] textOpen:[73, 76, "###"] text:[77, 90, "Heading 1.1.1"]
    Text[77, 90] chars:[77, 90, "Headi … 1.1.1"]
  Heading[91, 132] textOpen:[91, 94, "###"] text:[95, 132, "Heading 1.1.2  **_some bold italic_**"]
    Text[95, 110] chars:[95, 110, "Headi … 1.2  "]
    StrongEmphasis[110, 132] textOpen:[110, 112, "**"] text:[112, 130, "_some bold italic_"] textClose:[130, 132, "**"]
      Emphasis[112, 130] textOpen:[112, 113, "_"] text:[113, 129, "some bold italic"] textClose:[129, 130, "_"]
        Text[113, 129] chars:[113, 129, "some  … talic"]
````````````````````````````````


Text only, sorted

```````````````````````````````` example(Toc: 21) options(text-only, sorted)
[TOC] 

## Heading 1.1 _some italic_
# Heading **some bold** 1
### Heading 1.1.2  **_some bold italic_**
### Heading 1.1.1

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 some italic</a></li>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  some bold italic</a></li>
</ul>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 36] textOpen:[8, 10, "##"] text:[11, 36, "Heading 1.1 _some italic_"]
    Text[11, 23] chars:[11, 23, "Headi …  1.1 "]
    Emphasis[23, 36] textOpen:[23, 24, "_"] text:[24, 35, "some italic"] textClose:[35, 36, "_"]
      Text[24, 35] chars:[24, 35, "some  … talic"]
  Heading[37, 62] textOpen:[37, 38, "#"] text:[39, 62, "Heading **some bold** 1"]
    Text[39, 47] chars:[39, 47, "Heading "]
    StrongEmphasis[47, 60] textOpen:[47, 49, "**"] text:[49, 58, "some bold"] textClose:[58, 60, "**"]
      Text[49, 58] chars:[49, 58, "some bold"]
    Text[60, 62] chars:[60, 62, " 1"]
  Heading[63, 104] textOpen:[63, 66, "###"] text:[67, 104, "Heading 1.1.2  **_some bold italic_**"]
    Text[67, 82] chars:[67, 82, "Headi … 1.2  "]
    StrongEmphasis[82, 104] textOpen:[82, 84, "**"] text:[84, 102, "_some bold italic_"] textClose:[102, 104, "**"]
      Emphasis[84, 102] textOpen:[84, 85, "_"] text:[85, 101, "some bold italic"] textClose:[101, 102, "_"]
        Text[85, 101] chars:[85, 101, "some  … talic"]
  Heading[105, 122] textOpen:[105, 108, "###"] text:[109, 122, "Heading 1.1.1"]
    Text[109, 122] chars:[109, 122, "Headi … 1.1.1"]
````````````````````````````````


Text only, reverse sorted

```````````````````````````````` example(Toc: 22) options(text-only, sorted-reversed)
[TOC] 

## Heading 1.1 _some italic_
# Heading **some bold** 1
### Heading 1.1.2  **_some bold italic_**
### Heading 1.1.1

.
<ul>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  some bold italic</a></li>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-11-some-italic">Heading 1.1 some italic</a></li>
</ul>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h3 id="heading-111">Heading 1.1.1</h3>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 36] textOpen:[8, 10, "##"] text:[11, 36, "Heading 1.1 _some italic_"]
    Text[11, 23] chars:[11, 23, "Headi …  1.1 "]
    Emphasis[23, 36] textOpen:[23, 24, "_"] text:[24, 35, "some italic"] textClose:[35, 36, "_"]
      Text[24, 35] chars:[24, 35, "some  … talic"]
  Heading[37, 62] textOpen:[37, 38, "#"] text:[39, 62, "Heading **some bold** 1"]
    Text[39, 47] chars:[39, 47, "Heading "]
    StrongEmphasis[47, 60] textOpen:[47, 49, "**"] text:[49, 58, "some bold"] textClose:[58, 60, "**"]
      Text[49, 58] chars:[49, 58, "some bold"]
    Text[60, 62] chars:[60, 62, " 1"]
  Heading[63, 104] textOpen:[63, 66, "###"] text:[67, 104, "Heading 1.1.2  **_some bold italic_**"]
    Text[67, 82] chars:[67, 82, "Headi … 1.2  "]
    StrongEmphasis[82, 104] textOpen:[82, 84, "**"] text:[84, 102, "_some bold italic_"] textClose:[102, 104, "**"]
      Emphasis[84, 102] textOpen:[84, 85, "_"] text:[85, 101, "some bold italic"] textClose:[101, 102, "_"]
        Text[85, 101] chars:[85, 101, "some  … talic"]
  Heading[105, 122] textOpen:[105, 108, "###"] text:[109, 122, "Heading 1.1.1"]
    Text[109, 122] chars:[109, 122, "Headi … 1.1.1"]
````````````````````````````````


Text and inlines, sorted

```````````````````````````````` example(Toc: 23) options(sorted)
[TOC] 

### Heading 1.1.2  **_some bold italic_**
### Heading 1.1.1
## Heading 1.1 _some italic_
# Heading **some bold** 1

.
<ul>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a></li>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
</ul>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h3 id="heading-111">Heading 1.1.1</h3>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
.
Document[0, 124]
  TocBlock[0, 7] openingMarker:[0, 1] tocKeyword:[1, 4] closingMarker:[4, 5]
  Heading[8, 49] textOpen:[8, 11, "###"] text:[12, 49, "Heading 1.1.2  **_some bold italic_**"]
    Text[12, 27] chars:[12, 27, "Headi … 1.2  "]
    StrongEmphasis[27, 49] textOpen:[27, 29, "**"] text:[29, 47, "_some bold italic_"] textClose:[47, 49, "**"]
      Emphasis[29, 47] textOpen:[29, 30, "_"] text:[30, 46, "some bold italic"] textClose:[46, 47, "_"]
        Text[30, 46] chars:[30, 46, "some  … talic"]
  Heading[50, 67] textOpen:[50, 53, "###"] text:[54, 67, "Heading 1.1.1"]
    Text[54, 67] chars:[54, 67, "Headi … 1.1.1"]
  Heading[68, 96] textOpen:[68, 70, "##"] text:[71, 96, "Heading 1.1 _some italic_"]
    Text[71, 83] chars:[71, 83, "Headi …  1.1 "]
    Emphasis[83, 96] textOpen:[83, 84, "_"] text:[84, 95, "some italic"] textClose:[95, 96, "_"]
      Text[84, 95] chars:[84, 95, "some  … talic"]
  Heading[97, 122] textOpen:[97, 98, "#"] text:[99, 122, "Heading **some bold** 1"]
    Text[99, 107] chars:[99, 107, "Heading "]
    StrongEmphasis[107, 120] textOpen:[107, 109, "**"] text:[109, 118, "some bold"] textClose:[118, 120, "**"]
      Text[109, 118] chars:[109, 118, "some bold"]
    Text[120, 122] chars:[120, 122, " 1"]
````````````````````````````````


Text and inlines, unsorted

```````````````````````````````` example(Toc: 24) options(sorted)
[TOC flat] 

### Heading 1.1.2  **_some bold italic_**
## Heading 1.1 _some italic_
### Heading 1.1.1
# Heading **some bold** 1

.
<ul>
  <li><a href="#heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></a></li>
  <li><a href="#heading-11-some-italic">Heading 1.1 <em>some italic</em></a></li>
  <li><a href="#heading-111">Heading 1.1.1</a></li>
</ul>
<h3 id="heading-112--some-bold-italic">Heading 1.1.2  <strong><em>some bold italic</em></strong></h3>
<h2 id="heading-11-some-italic">Heading 1.1 <em>some italic</em></h2>
<h3 id="heading-111">Heading 1.1.1</h3>
<h1 id="heading-some-bold-1">Heading <strong>some bold</strong> 1</h1>
.
Document[0, 129]
  TocBlock[0, 12] openingMarker:[0, 1] tocKeyword:[1, 4] style:[5, 9] closingMarker:[9, 10]
  Heading[13, 54] textOpen:[13, 16, "###"] text:[17, 54, "Heading 1.1.2  **_some bold italic_**"]
    Text[17, 32] chars:[17, 32, "Headi … 1.2  "]
    StrongEmphasis[32, 54] textOpen:[32, 34, "**"] text:[34, 52, "_some bold italic_"] textClose:[52, 54, "**"]
      Emphasis[34, 52] textOpen:[34, 35, "_"] text:[35, 51, "some bold italic"] textClose:[51, 52, "_"]
        Text[35, 51] chars:[35, 51, "some  … talic"]
  Heading[55, 83] textOpen:[55, 57, "##"] text:[58, 83, "Heading 1.1 _some italic_"]
    Text[58, 70] chars:[58, 70, "Headi …  1.1 "]
    Emphasis[70, 83] textOpen:[70, 71, "_"] text:[71, 82, "some italic"] textClose:[82, 83, "_"]
      Text[71, 82] chars:[71, 82, "some  … talic"]
  Heading[84, 101] textOpen:[84, 87, "###"] text:[88, 101, "Heading 1.1.1"]
    Text[88, 101] chars:[88, 101, "Headi … 1.1.1"]
  Heading[102, 127] textOpen:[102, 103, "#"] text:[104, 127, "Heading **some bold** 1"]
    Text[104, 112] chars:[104, 112, "Heading "]
    StrongEmphasis[112, 125] textOpen:[112, 114, "**"] text:[114, 123, "some bold"] textClose:[123, 125, "**"]
      Text[114, 123] chars:[114, 123, "some bold"]
    Text[125, 127] chars:[125, 127, " 1"]
````````````````````````````````


## Source Position Attribute

```````````````````````````````` example(Source Position Attribute: 1) options(src-pos)
## Header 2
### Header 3

[TOC levels=3]
.
<h2 id="header-2" md-pos="3-11">Header 2</h2>
<h3 id="header-3" md-pos="16-24">Header 3</h3>
<div md-pos="26-40">
  <ul>
    <li><a href="#header-3">Header 3</a></li>
  </ul>
</div>
.
Document[0, 40]
  Heading[0, 11] textOpen:[0, 2, "##"] text:[3, 11, "Header 2"]
    Text[3, 11] chars:[3, 11, "Header 2"]
  Heading[12, 24] textOpen:[12, 15, "###"] text:[16, 24, "Header 3"]
    Text[16, 24] chars:[16, 24, "Header 3"]
  TocBlock[26, 40] openingMarker:[26, 27] tocKeyword:[27, 30] style:[31, 39] closingMarker:[39, 40]
````````````````````````````````


## Test unordered skipped headings

```````````````````````````````` example Test unordered skipped headings: 1
# Test 1

### test 0.0.1

### test 0.0.2

## test 1.1

### test 1.1.1

#### test 1.1.1.1

#### test 1.1.1.2

## test 1.2

### test 1.2.1

#### test 1.2.1.1

#### test 1.2.1.2

[TOC levels=2,4]

.
<h1 id="test-1">Test 1</h1>
<h3 id="test-001">test 0.0.1</h3>
<h3 id="test-002">test 0.0.2</h3>
<h2 id="test-11">test 1.1</h2>
<h3 id="test-111">test 1.1.1</h3>
<h4 id="test-1111">test 1.1.1.1</h4>
<h4 id="test-1112">test 1.1.1.2</h4>
<h2 id="test-12">test 1.2</h2>
<h3 id="test-121">test 1.2.1</h3>
<h4 id="test-1211">test 1.2.1.1</h4>
<h4 id="test-1212">test 1.2.1.2</h4>
<ul>
  <li><a href="#test-11">test 1.1</a>
    <ul>
      <li><a href="#test-1111">test 1.1.1.1</a></li>
      <li><a href="#test-1112">test 1.1.1.2</a></li>
    </ul>
  </li>
  <li><a href="#test-12">test 1.2</a>
    <ul>
      <li><a href="#test-1211">test 1.2.1.1</a></li>
      <li><a href="#test-1212">test 1.2.1.2</a></li>
    </ul>
  </li>
</ul>
.
Document[0, 194]
  Heading[0, 8] textOpen:[0, 1, "#"] text:[2, 8, "Test 1"]
    Text[2, 8] chars:[2, 8, "Test 1"]
  Heading[10, 24] textOpen:[10, 13, "###"] text:[14, 24, "test 0.0.1"]
    Text[14, 24] chars:[14, 24, "test 0.0.1"]
  Heading[26, 40] textOpen:[26, 29, "###"] text:[30, 40, "test 0.0.2"]
    Text[30, 40] chars:[30, 40, "test 0.0.2"]
  Heading[42, 53] textOpen:[42, 44, "##"] text:[45, 53, "test 1.1"]
    Text[45, 53] chars:[45, 53, "test 1.1"]
  Heading[55, 69] textOpen:[55, 58, "###"] text:[59, 69, "test 1.1.1"]
    Text[59, 69] chars:[59, 69, "test 1.1.1"]
  Heading[71, 88] textOpen:[71, 75, "####"] text:[76, 88, "test 1.1.1.1"]
    Text[76, 88] chars:[76, 88, "test  … 1.1.1"]
  Heading[90, 107] textOpen:[90, 94, "####"] text:[95, 107, "test 1.1.1.2"]
    Text[95, 107] chars:[95, 107, "test  … 1.1.2"]
  Heading[109, 120] textOpen:[109, 111, "##"] text:[112, 120, "test 1.2"]
    Text[112, 120] chars:[112, 120, "test 1.2"]
  Heading[122, 136] textOpen:[122, 125, "###"] text:[126, 136, "test 1.2.1"]
    Text[126, 136] chars:[126, 136, "test 1.2.1"]
  Heading[138, 155] textOpen:[138, 142, "####"] text:[143, 155, "test 1.2.1.1"]
    Text[143, 155] chars:[143, 155, "test  … 2.1.1"]
  Heading[157, 174] textOpen:[157, 161, "####"] text:[162, 174, "test 1.2.1.2"]
    Text[162, 174] chars:[162, 174, "test  … 2.1.2"]
  TocBlock[176, 193] openingMarker:[176, 177] tocKeyword:[177, 180] style:[181, 191] closingMarker:[191, 192]
````````````````````````````````


```````````````````````````````` example Test unordered skipped headings: 2
Common configuration for `its-base`-based plugins
=================================================

[TOC]

## Identifying ITS ids

In order to extract ITS ids from commit messages, @PLUGIN@ uses
[commentlink][upstream-comment-link-doc]s of
([per default][common-config-commentlink]) name "`@PLUGIN@`".

The ([per default][common-config-commentlinkGroupIndex]) first group of
`commentlink.@PLUGIN@.match` is considered the issue id.

So for example having

```
[commentlink "@PLUGIN@"]
    match = [Bb][Uu][Gg][ ]*([1-9][0-9]*)
    html = "<a href=\"http://my.issure.tracker.example.org/show_bug.cgi?id=$1\">(bug $1)</a>"
```

in `etc/gerrit.config` would allow to match the issues `4711`, `167`
from a commit message like

```
Sample commit message relating to bug 4711, and bug 167.
```

[upstream-comment-link-doc]: ../../../Documentation/config-gerrit.html#commentlink

By setting a `commentlink`'s `association` on the plugin's @PLUGIN@ configuration, it
is possible to require commits to carry ITS references; the following
values are supported (default is `OPTIONAL`):

MANDATORY
:→ One or more issue-ids are required in the git commit message.  The git push will
→ be rejected otherwise.

SUGGESTED
:→ Whenever the git commit message does not contain one or more issue-ids,
→ a warning message is displayed as a suggestion on the client.

OPTIONAL
:→ Bug-ids are liked when found in the git commit message, no warning is
→ displayed otherwise.

Example:

```
[plugin "@PLUGIN@"]
    association = MANDATORY
```

in `etc/gerrit.config` would accept only commits that contain a valid issue id
in the comment, matching the commentLink defined previously.

NOTE: Historically the association has been defined in the Gerrit's commentLink
section. That setting is deprecated but still supported for the current release.
You are encouraged to move the association policy to the plugin section, the
commentLink.association will be discontinued in the next major release.

The association can be overridden at project level in the project.config
using the same syntax used in the gerrit.config. Project's hierarchy will be respected
when evaluating the links configuration and association policy.

## Enabling ITS integration

It can be configured per project whether the issue tracker
integration is enabled or not. To enable the issue tracker integration
for a project the project must have the following entry in its
`project.config` file in the `refs/meta/config` branch:

```
  [plugin "@PLUGIN@"]
    enabled = true
```

If `plugin.@PLUGIN@.enabled` is not specified in the `project.config`
file the value is inherited from the parent project. If it is not
set on any parent project the issue integration is disabled for this
project.

By setting `plugin.@PLUGIN@.enabled` to true in the `project.config`
of the `All-Projects` project the issue tracker integration can be
enabled by default for all projects. During the initialization of the
plugin you are asked if the issue integration should be enabled by
default for all projects and if yes this setting in the
`project.config` of the `All-Projects` project is done automatically.

With this it is possible to support integration with multiple
issue tracker systems on a server. E.g. a project can choose if it
wants to enable integration with Jira or with Bugzilla.

If child projects must not be allowed to disable the issue tracker
system integration a project can enforce the issue tracker system
integration for all child projects by setting
`plugin.@PLUGIN@.enabled` to `enforced`.

The issue tracker system integration can be limited to specific
branches by setting `plugin.@PLUGIN@.branch`. The branches may be
configured using explicit ref names, ref patterns, or regular
expressions. Multiple branches may be specified.

E.g. to limit the issue tracker system integration to the `master`
branch and all stable branches the following could be configured:

```
  [plugin "@PLUGIN@"]
    enabled = true
    branch = refs/heads/master
    branch = ^refs/heads/stable-.*
```

## Associating a Gerrit project with its ITS project counterpart

To be able to make use of actions acting at the ITS project level, you must
associate a Gerrit project to its ITS project counterpart.

It must be configured per project and per plugin. To configure the association
for a project mapping to an ITS project named `manhattan-project`, the project
must have the following entry in its `project.config` file in the
`refs/meta/config` branch:

```
  [plugin "@PLUGIN@"]
    its-project = manhattan-project
```

## Configuring rules of when to take which actions in the ITS

Setting up which event in Gerrit (E.g.: “Change Merged”, or “User
‘John Doe’ voted ‘+2’ for ‘Code-Review’ on a change”) should trigger
which action on the ITS (e.g.: “Set issue's status to ‘Resolved’”) is
configured through a [rule base][rule-base] in
`etc/its/actions.config`.

[rule-base]: config-rulebase-common.md



## Multiple ITS

Although not a common setup the @PLUGIN@ plugin supports connecting
Gerrit to multiple issue tracking systems.

For example users may want to reference issues from two independent
issue tracking systems (i.e. a Bugzilla and a Jira instance).  In
this configuration you can simply install both its plugins and
configure them as described.

In situations where users want to reference issues from multiple
instances of the same issue tracking system (i.e. two independent
Bugzilla instances) they can simply create two its-bugzilla plugin
files with different names (i.e. its-bugzilla-external.jar and
its-bugzilla-internal.jar).  Gerrit will give each plugin the same
name as the file name (minus the extension).  You can view the names
by going to the Gerrit UI under menu Plugins -> Installed.  Now you
just need to use the appropriate name to configure each plugin.


## Further common configuration details

[common-config-commentlink]: #common-config-commentlink
[common-config-commentlinkGroupIndex]: #common-config-commentlinkGroupIndex

<a name="common-config-commentlink">`@PLUGIN@.commentlink`</a>
:   The name of the comment link to use to extract issue ids.

    This setting is useful to reuse the same comment link from different Its
    plugins. For example, if you set `@PLUGIN@.commentlink` to `foo`, then the
    comment link `foo` is used (instead of the comment link `@PLUGIN@`) to
    extract issue ids.

    Default is `@PLUGIN@`

<a name="common-config-commentlinkGroupIndex">`@PLUGIN@.commentlinkGroupIndex`</a>
:   The group index within `@PLUGIN@.commentlink` that holds the issue id.

    Default is `1`, if there are are groups within the regular expression for
    the `@PLUGIN@.commentlink` comment link, and the default is `0`, if there
    are no such groups.

<a name="common-config-dummyIssuePattern">`@PLUGIN@.dummyIssuePattern`</a>
:   Pattern which can be specified to match a dummy issue.

    This setting is useful to bypass the MANDATORY check for commits matching
    a specific pattern.

[Back to @PLUGIN@ documentation index][index]

[index]: index.html
.
<h1 id="common-configuration-for-its-base-based-plugins">Common configuration for <code>its-base</code>-based plugins</h1>
<ul>
  <li><a href="#identifying-its-ids">Identifying ITS ids</a></li>
  <li><a href="#enabling-its-integration">Enabling ITS integration</a></li>
  <li><a href="#associating-a-gerrit-project-with-its-its-project-counterpart">Associating a Gerrit project with its ITS project counterpart</a></li>
  <li><a href="#configuring-rules-of-when-to-take-which-actions-in-the-its">Configuring rules of when to take which actions in the ITS</a></li>
  <li><a href="#multiple-its">Multiple ITS</a></li>
  <li><a href="#further-common-configuration-details">Further common configuration details</a></li>
</ul>
<h2 id="identifying-its-ids">Identifying ITS ids</h2>
<p>In order to extract ITS ids from commit messages, @PLUGIN@ uses
<a href="../../../Documentation/config-gerrit.html#commentlink">commentlink</a>s of
(<a href="#common-config-commentlink">per default</a>) name &quot;<code>@PLUGIN@</code>&quot;.</p>
<p>The (<a href="#common-config-commentlinkGroupIndex">per default</a>) first group of
<code>commentlink.@PLUGIN@.match</code> is considered the issue id.</p>
<p>So for example having</p>
<pre><code>[commentlink &quot;@PLUGIN@&quot;]
    match = [Bb][Uu][Gg][ ]*([1-9][0-9]*)
    html = &quot;&lt;a href=\&quot;http://my.issure.tracker.example.org/show_bug.cgi?id=$1\&quot;&gt;(bug $1)&lt;/a&gt;&quot;
</code></pre>
<p>in <code>etc/gerrit.config</code> would allow to match the issues <code>4711</code>, <code>167</code>
from a commit message like</p>
<pre><code>Sample commit message relating to bug 4711, and bug 167.
</code></pre>
<p>By setting a <code>commentlink</code>'s <code>association</code> on the plugin's @PLUGIN@ configuration, it
is possible to require commits to carry ITS references; the following
values are supported (default is <code>OPTIONAL</code>):</p>
<p>MANDATORY
:→ One or more issue-ids are required in the git commit message.  The git push will
be rejected otherwise.</p>
<p>SUGGESTED
:→ Whenever the git commit message does not contain one or more issue-ids,
a warning message is displayed as a suggestion on the client.</p>
<p>OPTIONAL
:→ Bug-ids are liked when found in the git commit message, no warning is
displayed otherwise.</p>
<p>Example:</p>
<pre><code>[plugin &quot;@PLUGIN@&quot;]
    association = MANDATORY
</code></pre>
<p>in <code>etc/gerrit.config</code> would accept only commits that contain a valid issue id
in the comment, matching the commentLink defined previously.</p>
<p>NOTE: Historically the association has been defined in the Gerrit's commentLink
section. That setting is deprecated but still supported for the current release.
You are encouraged to move the association policy to the plugin section, the
commentLink.association will be discontinued in the next major release.</p>
<p>The association can be overridden at project level in the project.config
using the same syntax used in the gerrit.config. Project's hierarchy will be respected
when evaluating the links configuration and association policy.</p>
<h2 id="enabling-its-integration">Enabling ITS integration</h2>
<p>It can be configured per project whether the issue tracker
integration is enabled or not. To enable the issue tracker integration
for a project the project must have the following entry in its
<code>project.config</code> file in the <code>refs/meta/config</code> branch:</p>
<pre><code>  [plugin &quot;@PLUGIN@&quot;]
    enabled = true
</code></pre>
<p>If <code>plugin.@PLUGIN@.enabled</code> is not specified in the <code>project.config</code>
file the value is inherited from the parent project. If it is not
set on any parent project the issue integration is disabled for this
project.</p>
<p>By setting <code>plugin.@PLUGIN@.enabled</code> to true in the <code>project.config</code>
of the <code>All-Projects</code> project the issue tracker integration can be
enabled by default for all projects. During the initialization of the
plugin you are asked if the issue integration should be enabled by
default for all projects and if yes this setting in the
<code>project.config</code> of the <code>All-Projects</code> project is done automatically.</p>
<p>With this it is possible to support integration with multiple
issue tracker systems on a server. E.g. a project can choose if it
wants to enable integration with Jira or with Bugzilla.</p>
<p>If child projects must not be allowed to disable the issue tracker
system integration a project can enforce the issue tracker system
integration for all child projects by setting
<code>plugin.@PLUGIN@.enabled</code> to <code>enforced</code>.</p>
<p>The issue tracker system integration can be limited to specific
branches by setting <code>plugin.@PLUGIN@.branch</code>. The branches may be
configured using explicit ref names, ref patterns, or regular
expressions. Multiple branches may be specified.</p>
<p>E.g. to limit the issue tracker system integration to the <code>master</code>
branch and all stable branches the following could be configured:</p>
<pre><code>  [plugin &quot;@PLUGIN@&quot;]
    enabled = true
    branch = refs/heads/master
    branch = ^refs/heads/stable-.*
</code></pre>
<h2 id="associating-a-gerrit-project-with-its-its-project-counterpart">Associating a Gerrit project with its ITS project counterpart</h2>
<p>To be able to make use of actions acting at the ITS project level, you must
associate a Gerrit project to its ITS project counterpart.</p>
<p>It must be configured per project and per plugin. To configure the association
for a project mapping to an ITS project named <code>manhattan-project</code>, the project
must have the following entry in its <code>project.config</code> file in the
<code>refs/meta/config</code> branch:</p>
<pre><code>  [plugin &quot;@PLUGIN@&quot;]
    its-project = manhattan-project
</code></pre>
<h2 id="configuring-rules-of-when-to-take-which-actions-in-the-its">Configuring rules of when to take which actions in the ITS</h2>
<p>Setting up which event in Gerrit (E.g.: “Change Merged”, or “User
‘John Doe’ voted ‘+2’ for ‘Code-Review’ on a change”) should trigger
which action on the ITS (e.g.: “Set issue's status to ‘Resolved’”) is
configured through a <a href="config-rulebase-common.md">rule base</a> in
<code>etc/its/actions.config</code>.</p>
<h2 id="multiple-its">Multiple ITS</h2>
<p>Although not a common setup the @PLUGIN@ plugin supports connecting
Gerrit to multiple issue tracking systems.</p>
<p>For example users may want to reference issues from two independent
issue tracking systems (i.e. a Bugzilla and a Jira instance).  In
this configuration you can simply install both its plugins and
configure them as described.</p>
<p>In situations where users want to reference issues from multiple
instances of the same issue tracking system (i.e. two independent
Bugzilla instances) they can simply create two its-bugzilla plugin
files with different names (i.e. its-bugzilla-external.jar and
its-bugzilla-internal.jar).  Gerrit will give each plugin the same
name as the file name (minus the extension).  You can view the names
by going to the Gerrit UI under menu Plugins -&gt; Installed.  Now you
just need to use the appropriate name to configure each plugin.</p>
<h2 id="further-common-configuration-details">Further common configuration details</h2>
<p><a name="common-config-commentlink"><code>@PLUGIN@.commentlink</code></a>
:   The name of the comment link to use to extract issue ids.</p>
<pre><code>This setting is useful to reuse the same comment link from different Its
plugins. For example, if you set `@PLUGIN@.commentlink` to `foo`, then the
comment link `foo` is used (instead of the comment link `@PLUGIN@`) to
extract issue ids.

Default is `@PLUGIN@`
</code></pre>
<p><a name="common-config-commentlinkGroupIndex"><code>@PLUGIN@.commentlinkGroupIndex</code></a>
:   The group index within <code>@PLUGIN@.commentlink</code> that holds the issue id.</p>
<pre><code>Default is `1`, if there are are groups within the regular expression for
the `@PLUGIN@.commentlink` comment link, and the default is `0`, if there
are no such groups.
</code></pre>
<p><a name="common-config-dummyIssuePattern"><code>@PLUGIN@.dummyIssuePattern</code></a>
:   Pattern which can be specified to match a dummy issue.</p>
<pre><code>This setting is useful to bypass the MANDATORY check for commits matching
a specific pattern.
</code></pre>
<p><a href="index.html">Back to @PLUGIN@ documentation index</a></p>
````````````````````````````````


