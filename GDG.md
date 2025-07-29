**What is GDG? Why do we use GDG?**

GDG --> Generation Data Group

* Generation Data Groups (GDGs) are groups of datasets related to each other by a common name.
* The common name is GDG base and each dataset associated with the base is called a GDG version.
* A Maximum of 255 generations are allowed for a GDG base.

For example,

USERID.TEST.NEW.GDG is the GDG base name.

The datasets are named USERID.TEST.NEW.GDG.G0001V00, USERID.TEST.NEW.GDG.G0002V00 and so on.

G – Stands for Generation number – Value range 0000 – 9999
V – Stands for Version number – Value range 00 – 99

USES OF GDG:

--> We do not need to create a new JCL or change the name of the JCL every time in a weekly run or a daily run or monthly run or yearly run of a JCL.
--> You can set the limit of the related files(generations).
--> We can easily keep track of all generations of data sets.
--> We can delete or uncatalog the older generation.
--> Any particular generation can be referred to easily.

How to create a GDG Base?

--> Create a GDG base using IDCAMS utility – Access method service utility

/JOB1 JOB ...
//STEP1 EXEC PGM=IDCAMS
//SYSPRINT DD SYSOUT=A
//SYSIN DD
DEFINE GDG (NAME(USERID.TEST.NEW.GDG) -
EMPTY -
NOSCRATCH -
LIMIT(15))
/*

List of PARAMETERS used to create GDG:

NAME – Name of the GDG Base.
LIMIT – To limit the maximum number of generations.

EMPTY/NOEMPTY:

NOEMPTY – Uncatalog only the oldest generation in GDG when the limit is reached.
EMPTY – Uncatalog all the generations when a limit is reached.

SCRATCH/NOSCRATCH:

SCRATCH -Physically delete the dataset(generation) which is uncataloged.
NOSCRATCH – Don’t Physically delete the dataset(generation) which is uncataloged.

--> The current version of the GDG is referred to as USERID.TEST.NEW.GDG(0), Previous versions are referred to as (-1), (-2), and so on.
--> The next (new) version to be created in a program is referred to as USERID.TEST.NEW.GDG(+1).

How to create a new generation of a GDG?

Using the IEFBR14 utility, we create the new generations.

//JOB1 JOB ...
//STEP1 EXEC PGM=IEFBR14
//DD1 DD DSN=USERID.TEST.NEW.GDG(+1),DISP=(NEW,CATLG,DELETE),
// SPACE=(CYL,(5,2),RLSE),UNIT=SYSDA,
// DCB=(RECFM=FB,LRECL=100,BLSIZE=0)
//SYSPRINT DD SYSOUT=A
//SYSIN DD *
/*
