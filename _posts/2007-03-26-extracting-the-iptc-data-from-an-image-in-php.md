---
layout: single
title: Extracting the IPTC data from an image in PHP
date: 2007-03-26 10:08
categories: Development
tags: exif
---

<p align="left"><img src="/public/uploads/2007/03/image-missing.png" alt="image-missing" align="right" />When you add a caption to an image in <a href="http://picasa.google.com/">Google's Picasa/Picasa2</a> (and some other image editing programs) the caption is saved in a special spot in the imaged header section called IPTC data.</p>
While creating the <a href="http://www.abluestar.com/utilities/ephpg_iptc/">IPTC mod</a> for the <a href="/photo-gallery-that-does-not-require-a-mysql-database/">simple gallery script</a> I had to extract the IPTC information for the title of the image. This allowed me to extract the title from Picasa and included it under my images in my gallery.

<strong>What is IPTC?</strong>

IPTC stands for <a href="http://www.iptc.org/">International Press Telecommunications Council</a> and is a defined set of medadata mainly used in news organizations for copyright proposes.

Basically its a standard set of attributes for an image.

Some of the attributes that are included in this standard are; datesent, timesent, objectname, editstatus, urgency, category, subcategory, fixture, keyword, reldate, reltime, specinstr, credate, cretime, orgprg, prgver, byline, bytitle, city, sublocation, state, countrycode, countryname, orgtransref, <strong>headline</strong>, credit, <strong>source</strong>, copyright, contact, <strong>caption</strong>, captionwriter, imagetype, orientation, language, subfile, appreserve. for a full list see the <a href="http://www.iptc.org/IPTC7901/">REF document on IPTC.</a>

<strong>How to I extract IPTC information from an image?</strong>

Extracting and altering IPTC information in PHP is very simple with <a href="http://se2.php.net/manual/en/function.iptcparse.php">IPTCParse()</a> and <a href="http://se2.php.net/manual/en/function.iptcembed.php">IPTCEmbed()</a>

Example: View all available IPCT Data
<pre>function output_iptc_data( $image_path ) {
    $size = getimagesize ( $image_path, $info);
    if(is_array($info)) {
        $iptc = iptcparse($info["APP13"]);
        foreach (array_keys($iptc) as $s) {
            $c = count ($iptc[$s]);
            for ($i=0; $i &lt;$c; $i++)
            {
                echo $s.' = '.$iptc[$s][$i].'&lt;br&gt;';
            }
        }
    }
}</pre>
