# CustomLabels.ini

Вы можете присваивать меткам специфичные имена, которые не будут зависеть от [опций](../editor/options/formats.md#imena-metok) дизассемблера. Такие имена содержатся в файле `CustomLabels.ini` \(отдельный для каждого режима редактирования\).

Формат файла:   
`<адрес метки>=<имя>`

Если в дизассемблируемом файле есть метка по указанному адресу, она получит имя из файла.

Узнать адрес метки можно включив в [опциях](../editor/options/formats.md#imena-metok) формат меток `Смещение от начала`. После дизассемблирования файла, число после слова `Label` и будет адресом метки.
