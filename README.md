## Сборка проекта
Попытаемся собрать проект командой ```npm run build```. Получаем предупреждение и ошибку. 
```
WARNING in configuration
The 'mode' option has not been set, webpack will fallback to 'production' for this value. Set 'mode' option to 'development' or 'production' to enable defaults for each environment.

S2678: Type '"update"' is not comparable to type '"message" | "next" | "prev" | "restart" | "theme" | "timer"'.
```
Первое связано с отсутствием явного указания режима сборки проекта, исправим это, добавив ``--mode production`` к скрипту в ``package.json``.

Второе можно решить, добавив в файле ```src/application/actions.ts``` тип возвращаемого значения функции ``actionUpdate(...)`` к типу ``Action``, чтобы в файле ``src/application/data.ts`` не возникала ошибка из-за того, что в ``switch (action.type) {...}`` есть ``case 'update'``.

Пытаемся выполнить сборку ещё раз. Всё прошло успешно.