Отобразить окно на весь экран

`QWidget::showFullScreen()` is what you need - works great under Linux+Windows in my projects for years - but be careful, there shouldn't be two calls of this function (eg. first call of `QMainWindo->showFullScreen()` and then `MyWidget->showFullScreen()`).