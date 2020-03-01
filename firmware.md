
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



Didn't manage to load it into IDA Pro yet
