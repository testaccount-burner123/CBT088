# CBT088
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 088 is from Brian Westerman of Syzygy Inc. of Cary,       *   FILE 088
//*           North Carolina and Pismo Beach, California.           *   FILE 088
//*           The following is a list of what is in the file.       *   FILE 088
//*           This file is in IEBUPDTE SYSIN format.                *   FILE 088
//*                                                                 *   FILE 088
//*     My new address and phone number are                         *   FILE 088
//*                                                                 *   FILE 088
//*           Brian Westerman                                       *   FILE 088
//*           Syzygy Incorporated                                   *   FILE 088
//*           Director of Research and Development                  *   FILE 088
//*           897 Oak Park Blvd #500                                *   FILE 088
//*           Pismo Beach, CA  93449                                *   FILE 088
//*                                                                 *   FILE 088
//*           (800) 767-2244                                        *   FILE 088
//*           (800) 366-4082 - fax                                  *   FILE 088
//*                                                                 *   FILE 088
//*     email:    Brian_Westerman@SyzygyInc.com                     *   FILE 088
//*                                                                 *   FILE 088
//*   This is the File abstract as of 02/20/00.                     *   FILE 088
//*                                                                 *   FILE 088
//*   Unless otherwise noted, all programs support OS/390 V2.8      *   FILE 088
//*   and below (within reason)                                     *   FILE 088
//*                                                                 *   FILE 088
//*   Current Operating Systems at Syzygy (we support these         *   FILE 088
//*   for customer testing)                                         *   FILE 088
//*                                                                 *   FILE 088
//*               MVS 3.8E                                          *   FILE 088
//*               MVS/SP 1.3.6                                      *   FILE 088
//*               MVS/XA 2.2.3                                      *   FILE 088
//*               MVS/ESA 3.1                                       *   FILE 088
//*               MVS/ESA 4.3                                       *   FILE 088
//*               MVS/ESA 5.1                                       *   FILE 088
//*               OS/390 1.3                                        *   FILE 088
//*               OS/390 2.4                                        *   FILE 088
//*               OS/390 2.5                                        *   FILE 088
//*               OS/390 2.7                                        *   FILE 088
//*               OS/390 2.8                                        *   FILE 088
//*               OS/390 2.9  --- testing                           *   FILE 088
//*                                                                 *   FILE 088
//*   We also have various releases of VM, VM/ESA and DOS/VSE       *   FILE 088
//*   but they don't apply to this file.                            *   FILE 088
//*                                                                 *   FILE 088
//*   The following Items have been added as of 2/20/00.            *   FILE 088
//*                                                                 *   FILE 088
//*   AUTO  -  Automatic command and job scheduler.  This code      *   FILE 088
//*            was originaly on the CBT tape many years ago, but    *   FILE 088
//*            stopped working when MVS/ESA V5 came out because     *   FILE 088
//*            of some new ways of doing things with that version   *   FILE 088
//*            of MVS.  This program allows you to schedule jobs    *   FILE 088
//*            or commands to run at any time of day, any day of    *   FILE 088
//*            week any month of (well you get the picture).  It    *   FILE 088
//*            runs as a started task (time=1440) and you can use   *   FILE 088
//*            it to automatically schedule anything.  You can      *   FILE 088
//*            also fire off anything in it's files (by time or     *   FILE 088
//*            jobname) at any time.  There are 2 datasets that     *   FILE 088
//*            you will need to create, in the code they are        *   FILE 088
//*            SYZYGY.AUTO.COMMANDS and SYZYGY.AUTO.JOBS, (you      *   FILE 088
//*            should probably rename those) and the directions     *   FILE 088
//*            are easy to follow and are located in the first      *   FILE 088
//*            few hundred lines of hte code. We have used this     *   FILE 088
//*            as our ONLY scheduling system for years, and when    *   FILE 088
//*            we go to customer sites for contracts, we normally   *   FILE 088
//*            set it up for our stuff and the customer typically   *   FILE 088
//*            moves over to using it before we leave.  It's very   *   FILE 088
//*            easy to use and uses no resources.  You can give     *   FILE 088
//*            it a very high priority, (and probably should), we   *   FILE 088
//*            have thousands of jobs and commands scheduled with   *   FILE 088
//*            this guy every day, and it typically uses less       *   FILE 088
//*            than 1 minute (between 25 and 45 sec) of CPU time    *   FILE 088
//*            per month, (We IPL once per month wheather we need   *   FILE 088
//*            to or not). You can concatonate command and/or job   *   FILE 088
//*            libraries as needed so that you can have             *   FILE 088
//*            production and test jobs.  You can run as many       *   FILE 088
//*            copies of this little address space as you want      *   FILE 088
//*            for different purposes (test and production), but    *   FILE 088
//*            don't forget to use different command libraries      *   FILE 088
//*            because you will end up doing everything multiple    *   FILE 088
//*            times if you don't remember.                         *   FILE 088
//*                                                                 *   FILE 088
//*   COMMANDZ  -  This program was originally copied from          *   FILE 088
//*           the CBT tape and was originally written by John V.    *   FILE 088
//*           Hooper to execute a stack of commands to automate     *   FILE 088
//*           processing.  I have added a slew of code to this      *   FILE 088
//*           program so that now you can use it for scheduling     *   FILE 088
//*           and also I have included IF/Then logic parameters.    *   FILE 088
//*           The added code allows the following functions:        *   FILE 088
//*                                                                 *   FILE 088
//*           (A new copy has been supplied by Brian.  Please       *   FILE 088
//*            see member COMMAND@.)                                *   FILE 088
//*                                                                 *   FILE 088
//*           IFSTARTED JOBNAME - THIS GIVES THE ABILITY TO         *   FILE 088
//*                EXECUTE COMMANDS WHICH FOLLOW THIS COMMAND       *   FILE 088
//*                ONLY IF THE SPECIFIED JOBNAME IS ACTIVE.  THE    *   FILE 088
//*                ENDIF COMMAND ENDS THE IF NEST OF COMMANDS       *   FILE 088
//*                                                                 *   FILE 088
//*           IFSTOPPED JOBNAME - THIS GIVES THE ABILITY TO         *   FILE 088
//*                EXECUTE COMMANDS WHICH FOLLOW THIS COMMAND       *   FILE 088
//*                ONLY IF THE SPECIFIED JOBNAME IS NOT ACTIVE.     *   FILE 088
//*                THE ENDIF COMMAND ENDS THE IF NEST OF COMMANDS   *   FILE 088
//*                                                                 *   FILE 088
//*           WTO=TEXT  - ALLOWS YOU TO ISSUE WTOS OF ANYTHING      *   FILE 088
//*                YOU WANT TO SAY, UP TO 72 CHARACTERS THE         *   FILE 088
//*                FORMAT IS WTO=TEXT YOU WANT TO SAY               *   FILE 088
//*                                                                 *   FILE 088
//*           STOPCODE=NNNN -  ALLOWS YOU TO END PROCESSING         *   FILE 088
//*                AND OPTIONALLY SET A CONDITION CODE OF UP TO     *   FILE 088
//*                4 NUMERIC DIGITS.                                *   FILE 088
//*                THE FORMAT IS STOPCODE OR STOPCODE=NNNN WHERE    *   FILE 088
//*                NNNN IS FROM 1 TO 4 DIGITS, IF YOU SPECIFY MORE  *   FILE 088
//*                THAN 4 DIGITS, THE NUMBERS AFTER THE 4TH WILL    *   FILE 088
//*                BE IGNORED.                                      *   FILE 088
//*                                                                 *   FILE 088
//*   SHUTDOWN  -  Sample command file which shows how to use       *   FILE 088
//*           the new featurs of COMMANDZ to control the            *   FILE 088
//*           shutdown of the system.                               *   FILE 088
//*                                                                 *   FILE 088
//*   NOKEEP  -   This is an MPF exit which will COMPLETELY         *   FILE 088
//*           suppress messages from everywhere so you need to be   *   FILE 088
//*           careful, if you have messages that you have           *   FILE 088
//*           successfully kept from going to to console but        *   FILE 088
//*           still go to syslog then this is what you need.  We    *   FILE 088
//*           have a large phantom network and therefore we used    *   FILE 088
//*           to get over 1 million lines from VTAM/TCP about the   *   FILE 088
//*           nodes that were not up.  We used this little exit     *   FILE 088
//*           to keep from sending those to syslog and we have      *   FILE 088
//*           saved ourseleves a lot of time and it make looking    *   FILE 088
//*           for problems easier because you don't have to         *   FILE 088
//*           search around the useless messages in syslog.         *   FILE 088
//*                                                                 *   FILE 088
//*   REDMSG  -  This program was also originally from the CBT      *   FILE 088
//*           Tape, and was changed somewhat. It allows you to      *   FILE 088
//*           display a message on the console if the preceding     *   FILE 088
//*           step had a non-zero return code.                      *   FILE 088
//*                                                                 *   FILE 088
//*   SLSUX06 -  Storage Tek Silo Exit 6.  This code has also been  *   FILE 088
//*           given to STK as of 1/99 and will be distributed by    *   FILE 088
//*           them, but since I wrote it, I wanted to put it here   *   FILE 088
//*           as well.  This exit gets invoked on cartridge         *   FILE 088
//*           insert/eject processing.  We had a problem whereby    *   FILE 088
//*           when the operators printed the CA-1 scratch pick      *   FILE 088
//*           list, they didn't know which tapes were already in    *   FILE 088
//*           the silo and which ones were outside (and available   *   FILE 088
//*           to be picked).  This exit was already being used to   *   FILE 088
//*           flag tapes as scratch as soon as they were entered,   *   FILE 088
//*           (the one that STK has in their book and on the        *   FILE 088
//*           sample tapes does not work), so I changed it so that  *   FILE 088
//*           the tapes are now flagged as in or out of the silo.   *   FILE 088
//*           I had a talk with Computer Associates and they were   *   FILE 088
//*           nice enough to designate a flag which shows in or     *   FILE 088
//*           out of the silo, you can even show which silo it's    *   FILE 088
//*           in, (if you have more than 1) with this code.  It     *   FILE 088
//*           allows a lot of flexibility and has saved us the      *   FILE 088
//*           cost of a lot of operator overtime.  They also get    *   FILE 088
//*           less upset about who has to pick tapes now!           *   FILE 088
//*                                                                 *   FILE 088
//*   SYZYGYEJ  -  This program will take the output from a         *   FILE 088
//*           TMSGRW run and create SLUADMIN input to eject the     *   FILE 088
//*           tapes.  This is a follow on to the STK exit 6         *   FILE 088
//*           previously outlined.  The member SYZYGYE$ is the      *   FILE 088
//*           JCL for this program.                                 *   FILE 088
//*                                                                 *   FILE 088
//*   SYZYGYVR  -  This program will produce a VERY fast scratch    *   FILE 088
//*           listing and it is in a format which lends itself      *   FILE 088
//*           very nicely to multi columnizing with SAS for the     *   FILE 088
//*           operators to pick tapes from.                         *   FILE 088
//*                                                                 *   FILE 088
//*   MULTICOL -  Small SAS program from somewhere that             *   FILE 088
//*           demonstrates the multi column stuff for the           *   FILE 088
//*           SYZYGYVR program.                                     *   FILE 088
//*                                                                 *   FILE 088
//*   SYZREORG  -  Program which will greatly increase the speed    *   FILE 088
//*           of load/unload/reorg jobs for VSAM KSDS datasets.     *   FILE 088
//*           The buffers are altered automatically by the job      *   FILE 088
//*           which tends to increase the speed of the job by a     *   FILE 088
//*           great deal.  You can also do this by changing the     *   FILE 088
//*           JCL, but this is easier.                              *   FILE 088
//*                                                                 *   FILE 088
//*   The following files are also in this dataset:                 *   FILE 088
//*                                                                 *   FILE 088
//*     CATLIST - EXEC TO READ CATALOG AND CREATE A COMPLETE        *   FILE 088
//*               IDCAMS EXPORT JCL TO BACKUP ALL CATALOGS IN       *   FILE 088
//*               THE SYSTEM.  ANY TIME YOU CREATE A NEW            *   FILE 088
//*               CATALOG, (OR DELETE ONE) ALL YOU NEED TO DO       *   FILE 088
//*               IS RUN THE SYSBLD00 JOB WHICH EXECUTES THIS       *   FILE 088
//*               EXEC AND WILL BUILD A SYSCATBK JOBSTREAM.         *   FILE 088
//*               (ONE IS INCLUDED HERE AS WELL)                    *   FILE 088
//*                                                                 *   FILE 088
//*     EX8     - OS/390 COMPATABLE EXIT 8 FOR SENDING JOB END      *   FILE 088
//*               MAX COND CODE.  (SEE EXIT08 STUFF BELOW)          *   FILE 088
//*                                                                 *   FILE 088
//*     EX16    - OS/390 COMPATABLE EXIT 16 FOR SENDING JOB END     *   FILE 088
//*               MAX COND CODE.  (SEE EXIT16 STUFF BELOW)          *   FILE 088
//*                                                                 *   FILE 088
//*     EXIT004 - JCL SCAN EXIT (4) TO MAKE /** CARD A COMMENT      *   FILE 088
//*               (WE HAVE SOME PRETTY DUMB USERS, AND TO MAKE      *   FILE 088
//*               THE /*NOSETUP CARD A COMMENT SINCE WE USED TO     *   FILE 088
//*               REQUIRE EITHER A SETUP OR A NOSETUP IN THE        *   FILE 088
//*               PAST WE HAD TO AT LEAST IGNORE IT UNTIL OUR       *   FILE 088
//*               USERS CHANGED ALL OF THERE JCL (IT'S BEEN OVER    *   FILE 088
//*               A YEAR NOW AND THEY STILL SAY THAT THEY ARE       *   FILE 088
//*               WORKING ON IT!!!)                                 *   FILE 088
//*                                                                 *   FILE 088
//*     EXIT010 - NOTIFY EXIT (10) TO SEND THE JOB ENDED NOTIFY     *   FILE 088
//*               MESSAGE TO WYLBUR USERS WHO SUBMIT JOBS,  IT      *   FILE 088
//*               LOOKS FOR A NOTIFY MESSAGE FOR A WYLBUR USER      *   FILE 088
//*               AND REFORMATS IT INTO A F WYLBUR,TO XXXXXX        *   FILE 088
//*               AND THEN THE MESSAGE TEXT.                        *   FILE 088
//*                                                                 *   FILE 088
//*     EXITP20 - END OF JOB INPUT EXIT (20) WHICH WILL CAUSE A     *   FILE 088
//*               JOB TO BE ROUTED TO ANOTHER CPU IN A MULTI        *   FILE 088
//*               ACCESS SPOOL COMPLEX AUTOMATICALLY WITHOUT        *   FILE 088
//*               MAKING THE USER TYPE IN THE /*ROUTE STUFF         *   FILE 088
//*                                                                 *   FILE 088
//*     EXIT020 - END OF JOB INPUT EXIT (20) WHICH CHECKS THE       *   FILE 088
//*               JCT OF THE JOB ALSO THE JCL TO SE IF THE GUY      *   FILE 088
//*               ASKED FOR A SPECIAL PRIORITY AND IF SO HE WILL    *   FILE 088
//*               ISSUE A MESSAGE TO THE OPERATOR WHICH WILL BE     *   FILE 088
//*               HIGHLIGHTED AND NOT ROLL OFF THE SCREEN WHICH     *   FILE 088
//*               TELLS HIM THAT A SPECIAL PRIORITY JOB WAS         *   FILE 088
//*               SUBMITTED.                                        *   FILE 088
//*                                                                 *   FILE 088
//*     EX05... - 3   JES2 COMMAND EXITS (5) WHICH WILL DO          *   FILE 088
//*               VARIOUS THINGS LIKE NOT ALLOW THE OPERATOR TO     *   FILE 088
//*               PURGE THE ENTIRE QUEUE AND WILL DISPLAY JOB       *   FILE 088
//*               SETUPS WITH A COMMAND.                            *   FILE 088
//*                                                                 *   FILE 088
//*     EX005UD - JES2 EXIT(5) WHICH WILL GIVE YOU THE $UNDUMP      *   FILE 088
//*               COMMAND THIS ALLOWS YOU TO UNDO EVERTHING         *   FILE 088
//*               THAT YOU HAVE DONE WITH THE $DUMP COMMAND, SO     *   FILE 088
//*               THAT YOU DON'T HAVE TO DUMP AND RELOAD            *   FILE 088
//*               EVERTHING JUST BECAUSE YOU FORGOT A PARAMETER     *   FILE 088
//*               ON YOUR $DUMP COMMAND.                            *   FILE 088
//*                                                                 *   FILE 088
//*     JX05    - JES 2.2.0 VERSION OF THE ABOVE EX05... STUFF      *   FILE 088
//*                                                                 *   FILE 088
//*     J005$DV - JES 2.2.0 $DV COMMAND TO DISPLAY DASD VOLUMES     *   FILE 088
//*               FROM JES2                                         *   FILE 088
//*                                                                 *   FILE 088
//*     J005LOAD- JES 2.2.0 $LOAD COMMAND TO LOAD NEW COPIES OF     *   FILE 088
//*               EXITS                                             *   FILE 088
//*                                                                 *   FILE 088
//*     EXIT008 - JCT WRITE EXIT FOR JES2 EXIT(8) WHICH WILL        *   FILE 088
//*               PUT THE CONDITION CODE OF THE JOB STEP INTO       *   FILE 088
//*               THE JCT IF IT IS GREATER THAN WHAT IS ALREADY     *   FILE 088
//*               THERE.  THIS EXIT WORKS IN CONJUNCTION WITH       *   FILE 088
//*               EXIT016 AND EXIT008 MUST BE IN LPALIB.  IT IS     *   FILE 088
//*               VERY SMALL SO THERE IS LITTLE WORRY ABOUT         *   FILE 088
//*               PUTTING IT THERE.                                 *   FILE 088
//*                                                                 *   FILE 088
//*     JX08    - MVS/XA 2.2.0 VERSION OF EXIT008 ABOVE             *   FILE 088
//*                                                                 *   FILE 088
//*     EXIT016 - THIS JES EXIT(16) GETS INVOKED AT JOB             *   FILE 088
//*               TERMINATION AND WILL TAKE THE DATA PLACED IN      *   FILE 088
//*               THE JCT BY EXIT8 AND FORMAT A NOTIFY MESSAGE      *   FILE 088
//*               FOR TSO USERS AS TO THE MAX CONDITION CODE OF     *   FILE 088
//*               THE STEP AS WELL AS WHETHER IT ABENDED OR NOT     *   FILE 088
//*               WITH EITHER A SYSTEM OR USER ABEND. THE USERS     *   FILE 088
//*               ARE VERY PLEASED.                                 *   FILE 088
//*                                                                 *   FILE 088
//*     JX16    - JES 2.2.0 VERSION OF THE ABOVE EXIT016            *   FILE 088
//*                                                                 *   FILE 088
//*     EXIT212 - THIS JES EXIT(212) IS A DUMPER/LOADER EXIT        *   FILE 088
//*               WHICH ALLOWS YOU TO DYNAMICALLY ALLOCATE THE      *   FILE 088
//*               DUMPER/LOADER TAPE DSN INSTEAD OF ALWAYS          *   FILE 088
//*               HAVING TO HAVE A PRE-ALLOCATED TAPE DSN.          *   FILE 088
//*               THIS HAS SOLVED ALOT OF HEADACHES FOR THE         *   FILE 088
//*               OPERATIONS STAFF ... AND ME.  THIS REQUIRES       *   FILE 088
//*               THE PRCJ2212 USERMOD TO JES.  ALL THE MOD         *   FILE 088
//*               DOES IS ADD THE $EXIT POINT INTO HASPSTAM.        *   FILE 088
//*                                                                 *   FILE 088
//*     EX99 ---- PROGRAM USED BY PRCM0005 SYSMOD                   *   FILE 088
//*                                                                 *   FILE 088
//*     FINDASCB- PROGRAM INDEXES THROUGH ASVT AND WILL LOCATE      *   FILE 088
//*               A JOB OR ADDRESS SPACE WHO'S NAME MATCHES WHAT    *   FILE 088
//*               YOU PUT IN REG1.                                  *   FILE 088
//*                                                                 *   FILE 088
//*     GETINFO - PROGRAM ORIGINALLY FROM NTL BUT HAS SOME          *   FILE 088
//*               MINOR CHANGES AND ALSO HAS BEEN CHANGED TO        *   FILE 088
//*               RUN ON A MVS/SP SYSTEM INSTEAD OF OR I SHOULD     *   FILE 088
//*               SAY AS WELL AS MVS/XA.                            *   FILE 088
//*                                                                 *   FILE 088
//*     IEFACTRT- THIS IS PRETTY STANDARD STUFF EXCEPT THAT IT      *   FILE 088
//*               UPDATES THE JOBS OUTPUT RESOLUTION MESSAGE        *   FILE 088
//*               AREA WITH WHAT WE LIKE TO CALL "BOX SCORES".      *   FILE 088
//*               THIS IS SIMILAR TO WHAT IBM'S FREEBEE DOES        *   FILE 088
//*               BUT PUTS IT IN A BETTER PLACE.  YOU MAY WANT      *   FILE 088
//*               TO CHANGE SOME CODE SINCE WE ALSO DO A COUPLE     *   FILE 088
//*               OF CALCULATIONS TO TELL THE USER APPROXIMATELY    *   FILE 088
//*               WHAT THE JOB COST TO RUN.  THE CHARGE CODE IS     *   FILE 088
//*               VERY SIMPLE SO NO ONE SHOULD HAVE ANY             *   FILE 088
//*               PROBLEMS.                                         *   FILE 088
//*                                                                 *   FILE 088
//*     JES215MD- TWO MODS TO JES 2.1.5 THE FIRST IS TO HASPSSSM    *   FILE 088
//*               TO PUT THE DATE ON THE INITIATOR STARTED          *   FILE 088
//*               MESSAGE $HASP373 THE SECOND MOD IS TO HASPCOMM    *   FILE 088
//*               IT ALLOWS THE $D'JOBNAME COMMAND TO ACT AS A      *   FILE 088
//*               GENERIC JOBNAME DISPLAY IE. IF YOU ENTERED        *   FILE 088
//*               $D'IMS   , YOU WOULD GET A LIST OF ALL JOBS IN    *   FILE 088
//*               ALL QUEUES WHO'S PREFIX MATCHED THE LETTERS       *   FILE 088
//*               "IMS".  OPERATORS LIKE IT A LOT.                  *   FILE 088
//*                                                                 *   FILE 088
//*     MCS  ---- A VERY UNIQUE SPY COMMAND FROM ONE OF THE PRC     *   FILE 088
//*               SUBSIDIARIES.  I'M NOT SURE WHICH ONE, BUT I      *   FILE 088
//*               LIKE THE CODE.                                    *   FILE 088
//*                                                                 *   FILE 088
//*     MINIGEN - THE GOOD OLD MINIGEN, WE HAVE USED IT FOR         *   FILE 088
//*               YEARS AND CONTRARY TO POPULAR BELIEF IT CAN BE    *   FILE 088
//*               USED EVEN IF YOU ARE ADDING A NEW DEVICE TYPE.    *   FILE 088
//*               THE BEST WAY TO USE THIS GUY IS TO BROWSE YOUR    *   FILE 088
//*               STAGE1 OUTPUT AND FIND ALL OCCURRENCES OF "       *   FILE 088
//*               EXEC  ASMS"  THE MOD=XXXXXXX PARAMETER ON EACH    *   FILE 088
//*               ONE OF THESE GUYS SHOULD BE PUT IN THE ASSEM (    *   FILE 088
//*               SECTION OF THE MINIGEN.  THIS IS A HELL OF A      *   FILE 088
//*               LOT SAFER THAN A IOGEN AND THIS WAY WE NEVER      *   FILE 088
//*               LOSE ANY USERMODS                                 *   FILE 088
//*                                                                 *   FILE 088
//*     PANBKPRT- THIS GUY WILL TAKE A PANVALET BACKUP TAPE AND     *   FILE 088
//*               CREATE A LISTING OF WHAT PROGRAMS AND VERSIONS    *   FILE 088
//*               AND SIZE AND ALL IS ON THE TAPE. JUST AS IF IT    *   FILE 088
//*               WERE STILL ON DISK.  THIS WAY YOU DONT HAVE TO    *   FILE 088
//*               RESTORE THE WHOLE TAPE DOWN JUST TO FIND          *   FILE 088
//*               SOMTHING THAT YOU DON'T REALLY KNOW THE NAME      *   FILE 088
//*               OF OR EVEN GUESS AT.                              *   FILE 088
//*                                                                 *   FILE 088
//*     POSTER -- DOES WHAT IT SAYS, CREATES POSTERS-BANNERS.       *   FILE 088
//*                                                                 *   FILE 088
//*     PRCJ2001- JES2/SP 1.3.4 MOD TO ALLOW GENERIC $D'XXX' FOR    *   FILE 088
//*               PARTIAL JOBNAMES.                                 *   FILE 088
//*                                                                 *   FILE 088
//*     PRCJ2004- JES2/SP 1.3.4 MOD TO MAKE THE DEFAULT TSU AND     *   FILE 088
//*               STC MESSAGE CLASS A FOR JOBS THAT THEY SUBMIT.    *   FILE 088
//*               THIS ALLOWS YOU TO STILL SET THE &STCMCLAS AND    *   FILE 088
//*               &TSUMCLAS TO A DELETE CLASS TO KEEP FROM          *   FILE 088
//*               GETTING ALL OF THE USELESS JCL AND STILL NOT      *   FILE 088
//*               HAVE TO PUT A MSGCLASS= PARM ON ALL JOBCARDS.     *   FILE 088
//*               YOU DON'T NEED THIS IF YOU HAVE TSO/E FOR TSO     *   FILE 088
//*               BUT WE DON'T HAVE THE MONEY TO THROW AWAY ON      *   FILE 088
//*               THAT KIND OF PRODUCT AND WE ALSO HAVE A COUPLE    *   FILE 088
//*               OF STC'S THAT SUBMIT JOBS AND THIS HAS BEEN       *   FILE 088
//*               INDISPENSABLE.                                    *   FILE 088
//*                                                                 *   FILE 088
//*     PRCJ2212- JES2/SP 1.3.4 MOD TO ADD $EXIT 212 TO             *   FILE 088
//*               HASPSTAM FOR DYNAMIC DUMPER/LOADER DSN'S.         *   FILE 088
//*                                                                 *   FILE 088
//*     PRCM0001- SET IEALIMIT TO NOT GIVE ANY EXTRA MEMORY.        *   FILE 088
//*               IN MOST SHOPS POEPLE DON'T CARE ABOUT GIVING      *   FILE 088
//*               A JOB A LITTLE EXTRA, BUT OUR ACCOUNTING          *   FILE 088
//*               SYSTEM IS MEMORY INTENSIVE SO WE CAN'T ALLOW      *   FILE 088
//*               JOBS TO GET ANY MORE THAN THEY ASK FOR.           *   FILE 088
//*                                                                 *   FILE 088
//*     PRCM0002- THIS MOD WILL ALLOW DEFAULT TSO DYNAMIC           *   FILE 088
//*               ALLOCATION TO BE SHR INSTEAD OF OLD.  THIS IS     *   FILE 088
//*               FOR NON-TSO/E SYSTEMS, IF YOU HAVE TSO/E          *   FILE 088
//*               THERE IS ALREADY ANOTHER MOD ON THE CBT TAPE      *   FILE 088
//*               FOR THIS SAME TYPE OF THING. BUT IT IS ALOT       *   FILE 088
//*               BIGGER.  I GUESS THAT'S BECAUSE YOU HAVE TO       *   FILE 088
//*               ACTUALLY PAY FOR TSO/E.                           *   FILE 088
//*                                                                 *   FILE 088
//*     PRCM0003- THIS MOD MUST BE APPLIED WITH THE PRCM0004 MOD    *   FILE 088
//*     PRCM0004- WHICH IS ON THIS SAME FILE.  THE FIRST ONE IS A   *   FILE 088
//*               DUMMY MOD SO THAT I WILL BE INFORMED IF THERE     *   FILE 088
//*               IS ANY MAINTENANCE THAT EFFECTS THIS MOD BEFORE   *   FILE 088
//*               ITS TOO LATE.  YOU DON'T NEED TO PUT IT ON IF     *   FILE 088
//*               YOU DON'T WANT TO.  THIS MOD WILL PUT THE EXCP    *   FILE 088
//*               COUNTS ON THE IEF285I MESSAGE THAT COMES OUT ON   *   FILE 088
//*               YOUR JOB LISTING IE.                              *   FILE 088
//*                                                                 *   FILE 088
//*             IEF285I  C7BRIAN.VTOC.LOAD    KEPT     2123 EXCP    *   FILE 088
//*             IEF285I  DATASET.NAME         KEPT        0 EXCP    *   FILE 088
//*                                                                 *   FILE 088
//*     PRCM0005- MOD TO ALLOW YOU TO HAVE TSO DEFAULT ALLOCATE     *   FILE 088
//*               TO PACKS THAT ARE NOT MOUNTED AS PUBLIC OR        *   FILE 088
//*               STORAGE.  IT COMES WITH A PROGRAM CALLED EX99     *   FILE 088
//*               WHICH IS THE ACTUAL PCF EXIT THAT IS USED.        *   FILE 088
//*               YOU DO NOT HAVE TO HAVE PCF TO USE THIS MOD.      *   FILE 088
//*               WE DON'T HAVE IT AND WE RUN FINE.  YOU CAN        *   FILE 088
//*               SET THE ATTR2 FIELD IN THE PSCB TO ANY VOLUME     *   FILE 088
//*               THAT YOU WANT OR YOU CAN USE THE SETVOL           *   FILE 088
//*               PROGRAM ON THIS FILE TO DO IT FOR YOU             *   FILE 088
//*               AUTOMATICALLY                                     *   FILE 088
//*                                                                 *   FILE 088
//*     PRCM0010- THIS MOD WILL ELIMINATE THE DATASET NOT           *   FILE 088
//*               FREED; IS NOT ALLOCATED MESSAGE. FROM THE TSO     *   FILE 088
//*               ALLOC COMMAND.                                    *   FILE 088
//*                                                                 *   FILE 088
//*     PRCM0017- THIS MOD WILL ELIMINATE THE CN(00) BEING          *   FILE 088
//*               APPEND TO MESSAGES FROM THE OPERATOR AND ON       *   FILE 088
//*               THE NOTIFY OF JOB ENDED STUFF.                    *   FILE 088
//*                                                                 *   FILE 088
//*     TALK ---- CLIST TO DO ISPF FULL SCREEN SENDS TO PEOPLE      *   FILE 088
//*                                                                 *   FILE 088
//*     TALKP---- PANEL TO USE WITH THE TALK CLIST (PUT IT IN       *   FILE 088
//*               ISPPLIB CONCAT)                                   *   FILE 088
//*                                                                 *   FILE 088
//*     ULX..---- ISPF BASED VTOC ANALYSIS AND REPORTING            *   FILE 088
//*               FACILITY                                          *   FILE 088
//*                                                                 *   FILE 088
//*     USAGE   - TSO COMMAND TO DISPLAY SESSION COST.              *   FILE 088
//*                                                                 *   FILE 088
//*     WAITPROG- RUNS AS A BATHC JOB AND WILL ACCEPT A PARM        *   FILE 088
//*               THAT HAS THE NUMBER OF SECONDS THAT YOU WOULD     *   FILE 088
//*               LIKE TO WAIT AND DISPLAYS IT ON THE OS            *   FILE 088
//*               CONSOLE FOR THE OPERATOR IT HIGHLIGHTS IT AND     *   FILE 088
//*               WILL NOT ROLL OFF THE SCREEN.  WHEN THE TIME      *   FILE 088
//*               EXPIRES IT WILL ISSUE A DOM TO DELETE THE         *   FILE 088
//*               MESSAGE AND PUT OUT A REGULAR MESSAGE ABOUT       *   FILE 088
//*               REQUESTED TIME EXPIRED. THE JOBNAME IS ALSO       *   FILE 088
//*               PUT IN BOTH MESSAGES.                             *   FILE 088
//*                                                                 *   FILE 088
//*     XJ2PTP -- THIS IS A JES 2.1.5 EXIT TO DRAIN ALL OF THE      *   FILE 088
//*               TP LINES IN THE NETWORK WITH A SINGLE COMMAND     *   FILE 088
//*               $PTP. IT IS EXTREMELY USEFULL EVEN IF YOU         *   FILE 088
//*               DON'T HAVE OVER 600 LINES LIKE US.  YOU CAN       *   FILE 088
//*               ALSO START ALL TP WITH $STP OR RESTART WITH       *   FILE 088
//*               $ETP TO ACCOMPLISH A LOT OF WORK QUICKLY.         *   FILE 088
//*                                                                 *   FILE 088
//*     XJ2NET -- THIS IS A JES2 EXIT13 WHICH IS REQUIRED IF        *   FILE 088
//*               YOU WANT TO NOTIFY A TSO USER WHEN DATA IS        *   FILE 088
//*               RECEIVED FROM ANOTHER JES NODE. IT ADDS SOME      *   FILE 088
//*               NEAT STUFF LIKE HOW MANY LINES AND SUCH.          *   FILE 088
//*                                                                 *   FILE 088
//*     IEFUJV -- SMF UJV EXIT TO FORCE STANDARDS FOR MVS/XA        *   FILE 088
//*               2.2.0                                             *   FILE 088
//*                                                                 *   FILE 088
//*     ITACCTBL- TABLE USED BY THE MVS 2.2.0 VERSION OF IEFUJV     *   FILE 088
//*               FOR ACCOUNT #S                                    *   FILE 088
//*                                                                 *   FILE 088
//*     IEFUTL  - MVS/XA 2.2.0 SMF UTL EXIT                         *   FILE 088
//*                                                                 *   FILE 088
//*     IEFU29  - MVS/XA 2.2.0 SMF U29 EXIT                         *   FILE 088
//*                                                                 *   FILE 088
//*     IEFU83  - MVS/XA 2.2.0 SMF U83 EXIT                         *   FILE 088
//*                                                                 *   FILE 088
//*     IGGPRE00- MVS/XA 2.2.0 DADSM IGGPRE00 EXIT.  THIS EXIT      *   FILE 088
//*               USES 2 TABLES TSOTABL AND NODTABL WHICH ARE       *   FILE 088
//*               LOADED DYNAMICALLY AND CAN BE CHANGED ON THE      *   FILE 088
//*               FLY.  THIS EXIT WILL ALLOW STUFF TO BE            *   FILE 088
//*               ALLOCATED OR RENAMED ONLY TO THE PACKS WHICH      *   FILE 088
//*               WE DECIDE SHOULD GET THE PREFIXES.  THIS EXIT     *   FILE 088
//*               IS VERY POWERFUL AND IS EXTREMELY VERSATILE.      *   FILE 088
//*               THIS EXIT REQUIRES THE  MACROS CONNECT,           *   FILE 088
//*               EQUREGS, RELEASE, SETAMODE WHICH ARE ALSO         *   FILE 088
//*               INCLUDED IN THIS DATASET.                         *   FILE 088
//*                                                                 *   FILE 088
//*     NODTAB22- MVS/XA 2.2.0 VERSION OF THE NODETABLE FOR THE     *   FILE 088
//*               IGGPRE00 EXIT.  THIS ONE GOES IN LINKLIST.        *   FILE 088
//*                                                                 *   FILE 088
//*     TSOTAB22- MVS/XA 2.2.0 VERSION OF THE TSO UID TABLE FOR     *   FILE 088
//*               THE IGGPRE00 EXIT.  THIS ONE GOES IN LINKLIST.    *   FILE 088
//*                                                                 *   FILE 088
//*     Good Luck!                                                  *   FILE 088
//*                                                                 *   FILE 088
```
