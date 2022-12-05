# Create-COBOL-listing
Create a compiler listing with IGYCRCTL

write a JCL that would create a compiler listing with IGYCRCTL


Here is an example of a JCL script that could be used to create a compiler listing with IGYCRCTL:

 
//JOBNAME JOB (ACCT),'MY JOB',
//       MSGCLASS=H,
//       NOTIFY=&SYSUID
//*
//IGYCRCTL EXEC PGM=IGYCRCTL,
//       PARM='CSECT=MYPROGRAM,
//             COPY=MYCOPYBOOKS,
//             INFILE=MYINPUT.DAT,
//             OUTFILE=MYOUTPUT.DAT,
//             DBG=YES,
//             LIST'
//*
//MYPROGRAM EXEC PGM=MYPROGRAM
//*
//MYINPUT  DD DSN=MYINPUT.DAT,
//       DISP=SHR
//MYOUTPUT DD DSN=MYOUTPUT.DAT,
//       DISP=(NEW,CATLG),
//       SPACE=(TRK,(1,1)),
//       DCB=(RECFM=FB,LRECL=80)
//*
//SYSPRINT DD SYSOUT=*
//SYSUDUMP DD SYSOUT=*
//SYSIN    DD DUMMY



This JCL script specifies a batch job named JOBNAME that will be run under the ACCT account and will include the message MY JOB in the job log. It then defines several "steps" that will be executed as part of the job.

The first step, IGYCRCTL, specifies that the COBOL compiler program (PGM) named IGYCRCTL should be run with the specified parameters and options. In this case, the PARM option is used to pass the necessary options to the IGYCRCTL control card, including the name of the CSECT (MYPROGRAM), the location of the copybooks (COPY=MYCOPYBOOKS), the input and output files (INFILE and OUTFILE), debugging options (DBG=YES), and the LIST option to generate a compiler listing.

The second step, MYPROGRAM, specifies that the compiled COBOL program named MYPROGRAM should be run. This step assumes that the program has already been compiled using the IGYCRCTL step.

The remaining steps in the JCL script define the input and output files that will be used by the COBOL program. The MYINPUT and MYOUTPUT steps specify the names and locations of the input and output files, respectively, as well as their access modes and other details. The SYSPRINT, SYSUDUMP, and SYSIN steps are standard JCL steps that are used for various purposes, such as printing messages and handling errors.
