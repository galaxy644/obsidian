### **Точки**

Qpoint, Qpointf - Классы, задающие точки.

Qpointf p1( 10.2, 20.1);

Qpointf p2( 10.2, 20.1);

Qpointf p3=p1+p2 // (20.4, 40.2);

p3*2; // (41.2, 80.4);

p1.setX(3.1); p1.setY(2.1);

label->setText( QString::number(p1.rx())+” “+QString::number(p1.tx()));