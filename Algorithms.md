Сложность алгоритмов - это ключевой аспект при проектировании и создании веб-приложений, особенно при работе с большим объемом данных или выполнении вычислительно сложных операций. Понимание, как оценивать сложность алгоритмов, помогает принимать обоснованные решения в выборе алгоритмов и структур данных, а также оптимизировать производительность своих приложений

Big O - это термин из области анализа сложности алгоритмов и структур данных в информатике. Он используется для оценки верхней границы (наихудшего случая), временной сложности алгоритма. Простыми словами Big O показывает как будет меняться производительность алгоритма с зависимости от роста входящих данных.


Примеры нотаций Big O
 - **O(1)** : Константная сложность. Время выполнения алгоритма не зависит от размера входных данных. Например, доступ к элементу массива по индексу.
 - **O(log n)** : Логарифмическая сложность. Время выполнения алгоритма растет медленно с увеличением размера входных данных. Например, бинарный поиск в отсортированном массиве.
 - **O(n)** : Линейная сложность. Время выполнения алгоритма пропорционально размеру входных данных. Например, просмотр всех элементов в массиве.
 - **O(n log n)** : Линейно-логарифмическая сложность. Время выполнения алгоритма растет быстрее, чем линейно, но медленнее, чем квадратично. Например, сортировка слиянием (merge sort).
 - **O(n^2)** : Квадратичная сложность. Время выполнения алгоритма зависит от квадрата размера входных данных. Например, сортировка пузырьком (bubble sort).
 - **O(n^3)** : Кубическая сложность. Время выполнения алгоритма зависит от размера входных данных в кубе. Например, алгоритмы, которые имеют три вложенных цикла, такие как некоторые методы многомерной обработки данных.
 - **O(n!)** : Факториальная сложность. Это самая высокая степень роста времени выполнения алгоритма. Время выполнения алгоритма растет факториально от размера входных данных. Этот тип сложности встречается, например, при переборе всех возможных комбинаций элементов, что делает его чрезвычайно неэффективным для больших значений n.

![973455cf3bb354f49113562838372900](https://github.com/terhia/interview/assets/7370741/780e1b29-582c-4e68-9d38-7492669d5ad4)

**Selection sort** (сортировка выбором) – суть алгоритма заключается в проходе по массиву от начала до конца в поиске минимального элемента массива и перемещении его в начало. Сложность такого алгоритма **O(n^2)** .

**Bubble sort** (сортировка пузырьком) – данный алгоритм меняет местами два соседних элемента, если первый элемент массива больше второго. Так происходит до тех пор, пока алгоритм не обменяет местами все неотсортированные элементы. Сложность данного алгоритма сортировки равна **O(n^2)** .

**Insertion sort** (сортировка вставками) – алгоритм сортирует массив по мере прохождения по его элементам. На каждой итерации берется элемент и сравнивается с каждым элементом в уже отсортированной части массива, таким образом находя «свое место», после чего элемент вставляется на свою позицию. Так происходит до тех пор, пока алгоритм не пройдет по всему массиву. На выходе получим отсортированный массив. Сложность данного алгоритма равна **O(n^2)** .

**Quick sort** (быстрая сортировка) – суть алгоритма заключается в разделении массива на два под-массива, средней линией считается элемент, который находится в самом центре массива. В ходе работы алгоритма элементы, меньшие чем средний будут перемещены в лево, а большие в право. Такое же действие будет происходить рекурсивно и с под-массива, они будут разделяться на еще два под-массива до тех пор, пока не будет чего разделать (останется один элемент). На выходе получим отсортированный массив. Сложность алгоритма зависит от входных данных и в лучшем случае будет равняться O(n×2log2n). В худшем случае O(n^2). Существует также среднее значение, это **O(n×log2n)** .

**Comb sort** (сортировка расческой) – идея работы алгоритма крайне похожа на сортировку обменом, но главным отличием является то, что сравниваются не два соседних элемента, а элементы на промежутке, к примеру, в пять элементов. Это обеспечивает от избавления мелких значений в конце, что способствует ускорению сортировки в крупных массивах. Первая итерация совершается с шагом, рассчитанным по формуле (размер массива)/(фактор уменьшения), где фактор уменьшения равен приблизительно 1,247330950103979, или округлено до 1,3. Вторая и последующие итерации будут проходить с шагом (текущий шаг)/(фактор уменьшения) и будут происходить до тех пор, пока шаг не будет равен единице. Практически в любом случае сложность алгоритма равняется **O(n×log2n)** .
