<a id="top"></a>
<h3 align="center">BibleDB Data Cleaning Process</h3>

During the process of editing data, especially from files available on the internet, sometimes irregular characters are introduced into the text. The verse files in the BibleDB project have been cleaned as much as I've been able to clean them, but there's no guarantee that I've not missed or overlooked something that could cause a problem. This is a list of steps that I've taken to clean these files.

---

<br>

#### BibleDB Project - Steps to Clean the Verse Files

1. The process begins with the BibleDB project master database file named BibleDB.db. The BibleDB database files are available in the BibleDB repository on GitHub here: I will assume that you have setup your development environment according to the instructions here: [Development Environment Setup](/DEV/DEV.md).

2. Once these tools have been installed and properly set up data cleaning can begin, after you have downloaded the BibleDB files from here:  [BibleDB Project](https://github.com/ACB-Bible/BibleDB).

3. In the BibleDB/SQL-Queries/Maintenance folder there is an SQLite3 query file named Fix-Irregular-Data.sql, and it fixes some irregularities that I've found in the data files, but there may be others. This query can be run from the SQLite3 terminal, but I like to use the DB Browser Execute SQL functionality, so that's what I use.

4. Then open DB Browser App, go to the Execute SQL tab, and open the Fix-Irregular-Data.sql file, and execute it.

5. Under the files tab click on the Export Json button and export the SQL verses data to a Json file named TWFVerses.json, or any other prefix to Verses.json that matches one of the versions in the DATA/1-Misc/WorkVersions.json file. You can add any number of versions you want, after any verse data has been added to the BibleDB.db file, but the json idx key has to be in the proper order for the location within the json array, which is sorted alphebetically. If you add an entry to the WorkVersions.json file the id key must match the VersionID in the BibleDB.db verses table, and the idx key must reflect the location within the WorkVersions.json file json array. This means if you add a version to match the alphebetically sorted array, you will have to change the idx keys of all the values following the added entry, and the entry itself must have the same idx value as the entry that it is replacing. This is done to make accessing the entries easier for humans to find. Ineed to write an App to do this, but I haven't, maybe you could.

6. Once that's done, open the BibleDB folder with VSCode to access the NodeJS Javascript files, make sure you have installed NodeJS, and that you have added the VSCode profile lacated in the Bible-Code main directory. If you don't want to use this profile, you will have to install a VSCode extension to fix irregular white spaces, I use Fix Irregular Whitespaces by karlito40, or you can fix these irregularities manually.

7. In VSCode click on the View >> Command Palette button and search for fix irregular white space in current file. Select it and it will remove any unwanted characters from the file.

8. When that's done, you must minify the file, I use the VSCode extension MinifyAll by Jose Gracia Berenguer, which is already installed if you use the VSCode profile provided.

9. After the file is minified, it leaves some spacing problems within the file. So, then it's time to run the ZTransfer-Fix-min-JsonColon.js Javascript file in the BibleDB/JS/Transfer folder. Make sure you have NodeJS setup, and at the prompt in the VSCode terminal run this command:
``` node ZTransfer-Fix-min-JsonColon.js```

10. Your file is now as clean as I know how to make it.

---

<br>
   
#### The Bible Code Project

[Bible Code Project Documentation for Developers](https://github.com/ACB-Bible/Bible-Code/)
The "Bible Code Project" is a collection of GitHub repositories containing source code and data that can be used to develop your own computerized Bible project. All of the data and source code for each of these projects is in the public domain and free of copyrights, therefore it's free for you to use. The technical documentation for all of these projects is available in the Bible Code Project GitHub repository. If you to use any of the source code or data files in your own ministry or Bible project, please change the name of it, so people don't get confused.

[Back to Top](#top)

---

<br><br>
<p align="center">
    <p align="center">
    <em>God loves you, Jesus loves you, I love you, and this is God's free gift to you .....</em>
</p>    
</p>