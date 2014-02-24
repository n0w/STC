STC
===

STC (daemon) written in REXX to perform SQL queries and planify tasks

The main module (STCRXPPL) is loaded as STC. Then it loops, sleeping for 15 secs each iteration,
checking for command rows when awoken.

There are two kinds of command rows:

- PLANIFIED: Commands to be exectued certain days a week, at a specified time.
- NOT PLANIFIED: Commands to be executed on demand. Less-privileged users load these rows using 
an utility crafted for this purpose.

The GUI module allows to perform CRUD operations on the DB2 table, acting like an interface to the main module.
It can also wake the STC up by sending SIGCONT to its PID.

It looks like this:

 ``Command ===>                                                   Row 1 to 7 of 7 ``
``                          ·-----------------------------·                       ``
 ``(USRNME)                 | Panel de control STC @UAACC |       SCROLL  ===> PAG``
                          ``·-----------------------------·                       ``
                                                                                
  En la siguiente tabla se muestran todos los procesos planificados para        
  ejecucion.                                                                    
  Para dar de alta un nuevo proceso, escriba ALTA                               
  Para despertar la STC, escriba WAKE                                           
  Los comandos de linea posibles son:                                           
    I  - Informacion                                                            
    D  - Borrar                                                                 
                                                                                
  Sel     Dia      Hora                     Proceso                        Modo 
       ·-------·----------·-----------------------------------------------·----·
       |     1 |     6:05 |                       SIS.SDAADM.JCL(LOADPDT) |  S |
       ·-------·----------·-----------------------------------------------·----·
       |     2 |     6:05 |                       SIS.SDAADM.JCL(LOADPDT) |  S |
       ·-------·----------·-----------------------------------------------·----·
       |     3 |     6:05 |                       SIS.SDAADM.JCL(LOADPDT) |  S |
       ·-------·----------·-----------------------------------------------·----·
       |     4 |     6:05 |                      SIS.SDAADM.JCL(LOADPDT2) |  S |
       ·-------·----------·-----------------------------------------------·----·
       |     5 |     6:05 |                       SIS.SDAADM.JCL(LOADPDT) |  S |
       ·-------·----------·-----------------------------------------------·----·
       |     6 |     6:05 |                       SIS.SDAADM.JCL(LOADPDT) |  S |
       ·-------·----------·-----------------------------------------------·----·
       |     7 |     6:05 |                      SIS.SDAADM.JCL(LOADPDT2) |  S |
       ·-------·----------·-----------------------------------------------·----·
 ******************************* Bottom of data ********************************``
 
