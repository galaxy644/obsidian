==**Всё красиво, но непонятно. Разобрать потом !!!**==

struct team {  
string name;  
int humor_level, lough_level, fun_level, performance_level, audience_sympathy;  
long long score; // сумму баллов считаем один раз  

```Plain
team(string name, int humor, int lough, int fun, int performance, int sympathy)
    :name(name), humor_level(humor), lough_level(lough), fun_level(fun),
     performance_level(performance), audience_sympathy(sympathy),
     score(0LL + humor + lough + fun + performance + sympathy) // доп. суммируем баллы
    {}

friend ostream &operator<<(ostream &output, const team &t) { // перегруж. оператор вывода
     output << t.name << " " << t.humor_level << " " << t.lough_level << " ";
     output << t.fun_level << " " << t.performance_level << " " << t.audience_sympathy << endl;
     return output;
}
```

};

typedef bool (*comparator)(team &, team &); // тип comparator - указатель на функцию

bool better(team & t1, team & t2) { // условие выбора лучших команда  
return t1.score > t2.score || (t1.score == t2.score &&  
[t1.name](http://t1.name/) < [t2.name](http://t2.name/));  
}  

bool uglier(team & t1, team & t2) { // условие вывода в лексикографическом порядке  
return  
[t1.name](http://t1.name/) > [t2.name](http://t2.name/);  
}  

void bubble_sort(vector<team> & ts, comparator comp, int k) {  
int n = ts.size();  

```Plain
while (k--) { // ограничиваем сортировку до k последних элем.
    for (int j = 0, end = --n; j < end; ++j) {
        if (comp(ts[j], ts[j+1])) { swap(ts[j], ts[j+1]); }
    }
}
```

}

void to_final(vector<team> & ts, int k) {  
bubble_sort(ts, better, k); // сортируем по возрастанию баллов, k проходов  
vector<team> best(ts.begin() + (ts.size() - k), ts.end()); // копируем k лучших в вектор best  
bubble_sort(best, uglier, k); // сортируем лексикограф. по именам  

```Plain
for (auto t:best) { cout << t; }
```

}