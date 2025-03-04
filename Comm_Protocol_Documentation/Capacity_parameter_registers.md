# Capacity Parameter Registers

It was recently brought to our attention that the newest JBD desktop app lists capacity parameters in 10 percent increments.   
As far as we can remember, all of the apps used to list these parameters in 20 percent increments.    

I sniffed out the registers by using JBDTools -V2.9-20210524 to change each capacity parameter.   
I checked every firmware version that I could find in the shop.    

#### The following results are confirmed for:
* 4s BMSs with firmware 0x21 and 0x20    
* 16s BMSs with firmware 0x20    

| parameter | Register |
| :----: | :----: |
| End of voltage | 0x13 |
| 10% | 0x46 |
| 20% | 0x35 |
| 30% | 0x45 |
| 40% | 0x34 |
| 50% | 0x44 |
| 60% | 0x33 |
| 70% | 0x43 |
| 80% | 0x32 |
| 90% | 0x42 |
| 100% | 0x47 |
| Full voltage | 0x12 |

#### The following results are confirmed for:
* 4s BMSs with firmware 0x15     
* 8s BMSs with firmware 0x16

| parameter | Register |
| :----: | :----: |
| End of voltage | 0x13 |
| 10% | _note 1_ |
| 20% | 0x35 |
| 30% | _note 1_ |
| 40% | 0x34 |
| 50% | _note 1_ |
| 60% | 0x33 |
| 70% | _note 1_ |
| 80% | 0x32 |
| 90% | _note 2_ |
| 100% | _note 1_ |
| Full voltage | 0x12 |

Note 1:    
  No attempt was made by the JBD app to read this register.     
  I tried reading and writing these manually on the assumption that they would be the same as found on the newer firmware versions.   
  On attempting to write to these registers manually, the BMS reasponded "dd [register] 00 00 00 00 77"    
  Usually this means "ok" or "accepted", however on subsequent attempts to read this register manually    
  the BMS responded  "dd [register] 80 00 ff 80 77". Usually this means "fail" or "access denied"     
  
Note 2: The JBD app attempted to read but the BMS responded "dd [register] 80 00 ff 80 77". Usually this means "fail" or "access denied"    
