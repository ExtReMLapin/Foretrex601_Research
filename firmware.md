Based on firmware 3.5
# Firmware extraction



[The latest GCD file can be downloaded here](http://gawisp.com/perry/foretrex/Foretrex601_701_WebUpdater__350.gcd)

And you can extract the firmware using [RNG_Tool](http://www.gpsrchive.com/Oregon%207x0/files/RGN_Tool.exe) or [gcd-parser](https://github.com/mbirth/gcd-parser).


Which should give you those files

![](https://i.imgur.com/svw9Pv1.png)

fw_all.bin is the main firmware.


# Firmware Architecture

ARM Little-Endian


Source : 

```
$ binwalk -A fw_all.bin
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
5534          0x159E          ARM instructions, function prologue
12494         0x30CE          ARM instructions, function prologue
54198         0xD3B6          ARM instructions, function prologue
57006         0xDEAE          ARM instructions, function prologue
209898        0x333EA         ARM instructions, function prologue
327226        0x4FE3A         ARM instructions, function prologue
1440366       0x15FA6E        ARM instructions, function prologue
1474338       0x167F22        ARM instructions, function prologue
1475558       0x1683E6        ARM instructions, function prologue
1480918       0x1698D6        ARM instructions, function prologue
1536294       0x177126        ARM instructions, function prologue
1539834       0x177EFA        ARM instructions, function prologue
1570934       0x17F876        ARM instructions, function prologue
1630678       0x18E1D6        ARM instructions, function prologue
1635986       0x18F692        ARM instructions, function prologue
1642854       0x191166        ARM instructions, function prologue
```

Also string :  `..\..\..\TSK\garmin-os\arm\tsk_excptn_mngr.c`


You can dump the ram following [this turorial](https://www.gpspower.net/garmin-receivers-firmwares/277248-how-backup-nuvi-nv-region41-sd.html), it will not do what was expected but will create a crashdump file here `G:\GARMIN\DEBUG\ERR_LOG.TXT`

Inside the memory dump you can find this string : `MT3333 Software Version 2.50`


[Video showing how to load the whole thing in IDA](https://www.youtube.com/watch?v=wBGVtFK7Xfc)


## Sections list : 

```
.symtab
.strtab
.shstrtab
.interp
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.got
.got.plt
.data
.bss
.comment
```


# Supported languages


```
0:\Garmin\Text\french.ln3
0:\Garmin\Text\spanish.ln3
0:\Garmin\Text\german.ln3
0:\Garmin\Text\italian.ln3
0:\Garmin\Text\swedish.ln3
0:\Garmin\Text\danish.ln3
0:\Garmin\Text\norwegia.ln3
0:\Garmin\Text\dutch.ln3
0:\Garmin\Text\finnish.ln3
0:\Garmin\Text\polish.ln3
0:\Garmin\Text\czech.ln3
0:\Garmin\Text\croatia.ln3
0:\Garmin\Text\greek.ln3
0:\Garmin\Text\slovakia.ln3
0:\Garmin\Text\slovenia.ln3
0:\Garmin\Text\russian.ln3
0:\Garmin\Text\brazilia.ln3
0:\Garmin\Text\arabic.ln3
0:\Garmin\Text\turkish.ln3
```

# Other paths

```
0:\\GARMIN\\GPX\\WPT%i.gpx
0:\\GARMIN\\GPX\\WPT%i.gpx
0:\\GARMIN\\REMOTESW\\GUP2792.GCD
0:\\GARMIN\\REMOTESW\\GUP2792.GCD
0:/Garmin/AB
0:/Garmin/AB/PROFILE1.pro
0:/Garmin/REMOTESW
0:/Garmin/REMOTESW/EPOB.BIN
0:\Garmin\RemoteSW
0:\GARMIN\GARMIN~1.XML
0:\Garmin\GUPDATE.GCD
0:\GARMIN
0:\GARMIN\GPS
0:\GARMIN\GPS_SE~1.TXT
0:\GARMIN\GPS\GPS_LOG.csv
0:\GARMIN\GPS\gps_ttff.csv
0:/hopper.cfg
0:/nohopper.cfg
0:/hop.tmp
0:/hopper.log
0:/GARMIN/SNS_ERR.TXT
0:/GARMIN/SNS_ERR.BIN
0:/GARMIN/SNS_HUB.TXT
0:\Garmin\gmaptz.img
0:\TESTMODE.TXT
0:\GARMIN\EVNTLOGS\EVL.CMD
0:\GARMIN\EVNTLOGS
0:/GARMIN/REMOTESW/EPO.BIN
0:\GARMIN\GPX\RTE%i.gpx
0:\GARMIN\GPX\WPT%i.gpx
0:\Garmin
0:\AUTORUN.INF
0:\GARMIN\REMOTESW\GUP2792.GCD
0:/Garmin/GPX/Archive/
0:/Garmin/GPX/Current/
0:/Garmin/GPX/Temp/
0:/Garmin/
0:/Garmin/GPX/
0:\O_FILE.ERR
0:/Garmin/ACTIVITY/
0:/Garmin/GPX/Temp.gpx
0:/Garmin/GPX/Asset Tracks/
0:\Garmin\Debug
0:\Garmin\Debug\err_log.txt
```
