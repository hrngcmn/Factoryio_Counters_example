# Factoryio Counters Example
Bant konveyör üzerinden taşınan kutuların sayılır . Sayıcı saymasını tamamladığında ikaz lambası  yanar. Sayıcı saymasını tamamladığında konveyör durur.  Factory io bu işlemlerin simülasyonunu gerçek fabrika ortamı gibi bir alanda gösterir. Yapılan Plc programlamanın 3d olarak gözlemlenmesine olanak sağlar. 

* Simülasyonda çalıştırdığım için s7-1500 plc programlama yaptım. 
* Tia Portal programında ladder devresi oluşturulur. 
* Oluşturulan ladder diyagramı S7-PLCSIM e aktarılır. 
* Factory io ile S7PLC sim haberleştirmesi yapılır. 
* tia portal ve PLCSIM programlarının versiyon 16 ( V16) sürümü ile yapılmıştır. 
# Factory io projelendirilmesi

![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/Screenshot_1.png?raw=true)
## Pano görünümü:
Enerji stop tüm sistemin enerjisini durduracaktır. 
Start ile konveyör çalışmaya başlayacaktır.  Emiterden cisimler konveyöre inmeye başlayacak ve sensöre doğru hareket edeceklerdir.  
![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/Screenshot_2.png?raw=true)
## Sensörün konumlandırılması:
Sensör cisimleri görecek şekilde konulmalıdır. Sensör sayıcıya her lojik "1" verişinde sayıcının sayma değeri artacaktır. Sayıcı PV sine girilen değere ulaştığında sayıcı çıkışını aktif edecektir. 
![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/Screenshot_3.png?raw=true)
## ikaz lambası 
![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/Screenshot_4.png?raw=true)

# TIA PORTAL KODLAMASI
##  tag isimleri:
* Buton, sensör, motor, yardımcı röle, lamba gibi elektriksel elemanların tag isimlendirilmesini şu şekilde yaptım; 
* ![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/plctags.png?raw=true)
## Ladder diyagramı 
* **Network1** fabrika io da çalışması için templete dosyasının indirilmesi gerekir. Templete dosyası tia portalda açılır. Açılan templete dosyasının uzantısı olarak network 1 e de gözüken basamak gelir. 
* **Network2** start butonuna basılınca yardımcı rölenin set edilmesini sağlar. 
* **Network 3** stop butonuna baslınca yardımcı rölenin reset edilmesini sağlar. 


![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/network%201%20-%202-%203.png?raw=true)
* **Network4** konveyör start butonuna basılınca enerjilenir. Sayıcı sayma işlemini bitirdiğinde konveyörün enerjisi kesilir. 
* **Network5** Sayıcı sadece konveyör hareket halinde iken sayma gerçekleştirir. Sensörün cisim görmesi halinde sayıcı sayma değeri +1 olur. Girilen PV değerine ulaşıldığında sayıcının çıkışı aktif olacaktır. Böylece ikaz lambası yanar. 

![enter image description here](https://github.com/hrngcmn/Factoryio_Counters_exemple/blob/main/Screenshot_5.png?raw=true)

NOT: Sayıcının resetlenmesini enerji stop butonu ile gerçekleştirmedim. Ayrı bir reset butonu ile gerçekleşir. 


