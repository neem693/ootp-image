Important changes to the logos system in version 16!

Several changes were made to the logos system. We added them to the documentation below and here is a brief overview:
- all logos, jerseys and ballcaps folders may optionally have subfolders for cities and nicknames.
- city and nickname files will only be searched in these subfolders
- caps and jerseys texture files used to require two underlines in their file names due to a bug in OOTP. That was changed now.


Whenever you create a league, each team get's team colors and logos assigned to it. We've added some features which might be interesting for "modders":

The following table shows where OOTP looks for files and where it copies the found file:

Source folders                                                 -> league folder & file name
-----------------------------------------------------------------------------------------------------------------------------------------
Team logos: /data/logos or user defined logos folder           -> /"league name".lg/news/html/images/team_logos/"team name_nick name".png
Small team logos: /data/logos or user defined logos folder     -> /"league name".lg/news/html/images/team_logos/"team name_nick name"_small.png
Team jerseys: /data/jerseys or user defined jerseys folder     -> /"league name".lg/jerseys/jerseys_"team name_nick name".png
Team ball caps: /data/ballcaps or user defined ballcaps folder -> /"league name".lg/ballcaps/caps_"team name_nick name".png

Optional sub folders:

/data/logos/cities 
/data/logos/nicknames

/data/jerseys/cities
/data/jerseys/nicknames

/data/ballcaps/cities
/data/ballcaps/nicknames

OOTP will only use the /cities sub folders when looking for cities, so place files like jerseys_baltimore.png in /cities. Same for nicknames: OOTP will only use the /nicknames sub folders when looking for team nick names, so place files like jerseys_aces.png in /nicknames. 


The default names for these files are determind as follows:

 - Add a underscore to the team name.
 - Add the nickname.
 - Remove all periods.
 - The following characters will be replaced with an underscore "_": spaces " ' / \ : * ? < > | & ,
 - Add .png
 - Make all lowercase.

So for example the files for the St. Louis Cardinals would be st_louis_cardinals.png (logo file), jerseys_st_louis_cardinals.png and caps_st_louis_cardinals.png

OOTP has a neat, little-known capability, where you can use the logo file name to define a team's colors too. This means that just by loading a team logo, you can avoid all of that manual setup! Here's how it works. A logo file name might look something like this:

boston_cannibals.png

You can append up to eight different values to the end of the file name, separated by underscores ("_"), that tell the game what team colors you want to use. The appended values are hexadecimal color codes, 6 characters long, and represent the RGB (red, green, and blue) color codes for the color you wish to use. For example, you could do something like this:

boston_cannibals_FF0000_00FF00.png

This means that any team using the Boston Cannibals' logo should have a team background color of #FF0000 (which is red) and a text color of #00FF00 (which is green). You can repeat this process for up to nine values, as follows:

Team background color
Team text color
Team secondary color (not used)
Ballcap main color
Ballcap visor color
Jersey main color
Jersey secondary color
Jersey pin stripe color
Jersey away color

Jersey texture files can come with up to four color codes:

Jersey main color
Jersey secondary color
Jersey pin stripe color
Jersey away color

Ball cap texture files support two color codes:

Ballcap main color
Ballcap visor color

If the files come with color codes, there has to be a minimum of two color codes. So it's either no color codes, two color codes, or a number greater than two (max 9 for logos, max 4 for jerseys and max 2 for caps).

If a team logo has only two color codes "background color" and "text color", it will automatically use these codes for the missing colors this way:

Team secondary color (not used) = Team text color
Ballcap main color 		= Team background color
Ballcap visor color 		= Team text color
Jersey main color		= Team background color
Jersey secondary color 		= Team text color
Jersey pin stripe color 	= Team text color
Jersey away color 		= Team background color

Hint: the team color dialog has a "Select" link for each color, which opens a color edit dialog. The dialog contains the team logo. Click anywhere in the logo to "pick" a color!

OOTP will even look for color-matching jerseys and caps! For example if there are multiple cap texture files matching for a team, it will choose the cap texture file which comes with two color codes, which are identical with the team's ballcap colors.

Example:
1: /logos/nicknames/aces_FF0000_00FF00.png
2: /logos/nicknames/aces_FF0000_0000AA.png
3: /jerseys/nicknames/aces_FF0000_00FF00.png
4: /jerseys/nicknames/aces_FF0000_0000AA.png
5: /ballcaps/nicknames/aces_FF0000_00FF00.png
6: /ballcaps/nicknames/aces_FF0000_0000AA.png

If OOTP chose the first file as the logo for a team, it will also chose #3 and #5 for the jerseys and ballcaps. So the color schemes will match. The great "Nicknames Project" (see www.ootpmods.com) will support this feature.

In OOTP, you can also add years to the logo, jerseys and caps files. These are the correct formats:

team name_nick name.png
team name_nick name_1111.png
team name_nick name_1111_any text or color codes.png
team name_nick name_1111-2222.png
team name_nick name_1111-2222_any text or color codes.png

1111 = first year
2222 = second year (must be greater than first year)

For example there are the following files in the /logos folder:
boston_cannibals.png
boston_cannibals_1871-2008.png
boston_cannibals_2008-2010.png
boston_cannibals_2010-2011.png
boston_cannibals_2011.png

If the current game year in simulation is 2000, OOTP would use the file boston_cannibals_1871-2008.png.
In game year 2009, OOTP would use boston_cannibals_2008-2010.png
In game year 2010, OOTP would use boston_cannibals_2010-2011.png
In game year 2011, OOTP would use boston_cannibals_2011.png
In game year 2012, OOTP would use boston_cannibals.png

The file names can also contain color codes and commentary notes:
boston_cannibals_2010-2011_ffffff_00372A_some commentary.png 

OOTP supports optional small logos. Small logos will be used in-game for image sizes of 50x50 pixels or smaller. They reside in the same folder than the main logos (data/logos). Naming is the same as for the main logos but with a trailing "_small_50". 

Examples:
san_diego_padres_small_50.png
san_diego_padres_1985_small_50.png
san_diego_padres_1986-1989_small_50.png

No extra color codes are allowed for small logos.
If a team has no small log, it will use the main logo for smaller logo pictures.
If a team has no custom ballcap texture and uses a default texture for this reason, it will automatically use the small logo as ballcap logo.

You can remove the small logo from a team in the team color dialog.

Hint: the team color dialog contains several "Select" buttons to "import" logo or texture files from disk. They will be renamed and copied into the proper saved game folders. The dialog has a "Favorites" menu which will bring you quickly to certain often needed folders. Furthermore there's an ""Open" button which will open the current folder in your OS's file explorer, or the current file with the corresponding software (if installed). And there's a "Filter" button: click onit, enter the filter string (or click on a button to automatically select the team name or city) and hit Enter to filter the file list.

Special flag file for quickstart games:
The problem with the quickstart games is that they may contain info like jersey IDs and logo file names and so on from the computer where they were created on. OOTP has to reset this information to load the correct logos.
But a quickstart game could also come with logos and jerseys, in which case OOTP should NOT reset the logo info. So we added a flag file now. The file name is reset_picture_info.flag and the content doesn't matter. If this file exists inside the quickstart archive or folder when loading a quickstart game, OOTP will automatically reset all picture info and it will then delete the file from the new saved game.


Several teams did not have a logo during their first years, so we used the first logos of these teams.

These files have been used as a replacement:		These logos were missing:
---------------------------------------------------------------------------------------------------------
baltimore_orioles_1954-1965_FF671F_2D2926.png		baltimore_orioles_1875-1902_FC4C02_2D2926.png	
baltimore_orioles_1954-1965_small_50.png		baltimore_orioles_1875-1902_small_50.png	
boston_americans_1901-1907_00205B_FFFFFF.png		boston_americans_1901-1907_small_50.png	
chicago_white_sox_1902-1917_0C2340_FFFFFF.png		chicago_orphans_1900-1902_0C2340_FFFFFF.png	
chicago_white_sox_1902-1917_small_50.png		chicago_orphans_1900-1902_small_50.png	
chicago_white_sox_1902-1917_0C2340_FFFFFF.png		chicago_white_sox_1901_0C2340_FFFFFF.png	
chicago_white_sox_1902-1917_small_50.png		chicago_white_sox_1901_small_50.png	
cleveland_blues_1901_0C2340_FFFFFF.png			cleveland_blues_1901_small_50.png	
milwaukee_brewers_0A2351_B6922E.png			milwaukee_brewers_1900-1901_2E1A47_FFFFFF.png	
milwaukee_brewers_small_50.png				milwaukee_brewers_1900-1901_small_50.png	
washington_senators_1905-1927_0C2340_2D2926.png		washington_senators_1901-1904_2D2926_FFFFFF.png	
washington_senators_1905-1927_small_50.png		washington_senators_1901-1904_small_50.png	

