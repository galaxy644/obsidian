  
Работает на всех пинах, кроме GPIO16.  
Разрядность ШИМ по умолчанию 8 бит (0.. 255) на версиях ядра 3.x. На ранних версиях – 10 бит (0.. 1023).  
Разрядность можно настроить в analogWriteResolution(4...16 бит).  
Частота ШИМ по умолчанию 1 кГц.  
Частоту можно настроить в analogWriteFreq(100.. 40000 Гц).  
ШИМ реализован программно, поэтому на повышенной частоте и разрядности будет тормозить выполнение программы!