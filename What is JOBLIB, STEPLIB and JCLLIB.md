**What is JOBLIB, STEPLIB and JCLLIB ?**

-> In Job Control Language (JCL) for mainframe systems, JCLLIB, JOBLIB, and STEPLIB are DD statements used to specify libraries where the system can find programs to be executed.
--> These statements play a crucial role in the job execution process by guiding the system to the correct location of the load modules.

--> JCLLIB : Specifies a library that contains cataloged procedures.
//JCLLIB DD DSN=SYS1.PROCLIB,DISP=SHR

--> JOBLIB : Specifies a library that contains load modules for programs to be executed in the job.
//JOBLIB DD DSN=MY.LOADLIB,DISP=SHR

--> STEPLIB : Specifies a library that contains load modules for programs to be executed in a specific step of the job.
//STEP01 EXEC PGM=MYPROGRAM
//STEPLIB DD DSN=MY.STEP.LOADLIB,DISP=SHR

When the system searches for a program to execute, it follows this order:

--> STEPLIB: If a STEPLIB is specified for a step, the system searches that library first.
--> JOBLIB: If no STEPLIB is specified or the program is not found in the STEPLIB, the system searches the JOBLIB.
--> System Libraries: If the program is not found in either STEPLIB or JOBLIB, the system searches its default system libraries.

Key points:
* STEPLIB takes precedence over JOBLIB.
* Both JOBLIB and STEPLIB can contain multiple libraries, separated by commas.
* JCLLIB is used for cataloged procedures, while JOBLIB and STEPLIB are used for load modules.


