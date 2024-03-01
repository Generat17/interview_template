# Junior

### Устные вопросы (алгоритмы):
1) Какие деревья ты знаешь (структуры данных)?
```
1) Бинарное (двоичное)  дерево
2) Красно-чёрное дерево
3) АВЛ-дерево
4) B-дерево (2-3-дерево, B+-деревья, B*-дерево, UB-дерево)
5) Дерево Фенвика (Fenwick Tree)
6) Суффиксное дерево
7) Префиксное дерево (trie)
8) Сжатое префиксное дерево (radix)
9) Дерево Фибоначчи
10) Дерево отрезков (Segment Tree)

Много различных вариантов ответа. Обычно называют первые 4 дерева. Можно спросить подрбонее.
```
2) Чем отличается сбалансированное дерево от несбалансированного?
```
1) Сбалансированное дерево:
Все поддеревья имеют примерно одинаковую высоту.
Гарантируется, что операции вставки, удаления и поиска выполняются за логарифмическое время.
Примеры: AVL-дерево, красно-чёрное дерево.

2) Несбалансированное дерево:
Высота поддеревьев может сильно отличаться.
Операции могут выполняться за линейное время или хуже.
```
3) Какие алгоритмы сортировки существуют, и какова их сложность в нотации Big O?
```
1) Сортировка пузырьком (Bubble Sort) - O(n^2)
2) Сортировка вставками (Insertion Sort) - O(n^2)
3) Сортировка выбором (Selection Sort) - O(n^2)
4) Сортировка слиянием (Merge Sort) - O(n log n)
5) Быстрая сортировка (Quick Sort) - O(n log n)
6) Сортировка кучей (Heap Sort) - O(n log n)
```
4) В чем заключаются различия между устойчивыми и неустойчивыми алгоритмами сортировки?
```
1) Устойчивые алгоритмы сортировки:
Сохраняют порядок равных элементов: Если два элемента равны, то их относительный порядок не меняется.
Пример: Сортировка слиянием.
	
2) Неустойчивые алгоритмы сортировки:
Не гарантируют сохранение порядка равных элементов: Порядок равных элементов может измениться.
Пример: Быстрая сортировка.
```

### Практические задачи (алгоритмы):

1) Задача "Квадраты отсортированного массива"

https://leetcode.com/problems/squares-of-a-sorted-array/description/
```
Задан целочисленный массив nums, отсортированный в порядке неубывания.
Реализовать функцию, которая возвращает массив квадратов этих чисел, отсортированный в порядке неубывания.
Требуется наилучшее решение по времени выполнения.

Пример 1
Ввод: nums = [-4,-1,0,3,10]
Вывод: [0,1,9,16,100]

Пример 2
Ввод: nums = [-7,-3,2,3,11]
Вывод: [4,9,9,49,121]
```
Исходные данные:
```go
func sortedSquares(nums []int) []int {
    
}
```
Пример решения O(n):
```go
func sortedSquares(nums []int) []int {
    n := len(nums)-1
    result := make([]int, len(nums))

    for i, j := 0, n; n >= 0; n-- {     
        if nums[i] < 0 && -nums[i] >= nums[j] {
            result[n] = nums[i] * nums[i]
            i++
        } else {
            result[n] = nums[j] * nums[j]
            j--
        }
    }
    
    return result
}
```

2) Задача "Наибольший общий префикс"

https://leetcode.com/problems/longest-common-prefix
```
Реализовать функцию, которая находит самый длинный общий префикс среди элементов массива строк. 
Если такого префикса нет, программа должна вернуть пустую строку.

Пример 1
Ввод: strs = ["flower", "flow", "flight"]
Вывод: "fl"

Пример 2
Ввод: strs = ["dog", "racecar", "car"]
Вывод: ""

Ограничения:
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] состоит только из строчных английских букв.
```
Исходные данные:
```go
func longestCommonPrefix(strs []string) string {
    
}
```
Пример решения (№1) O(n*m):
```go
func longestCommonPrefix(strs []string) string {
    p := strs[0]
    
    for _, v := range strs {
        i := 0
        for ; i < len(v) && i < len(p) && p[i] == v[i]; i++ {}
        p = p[:i] 
    }

    return p
}
```

Пример решения (№2) O(n*m):
```go
func longestCommonPrefix(strs []string) string {
    for i := range strs[0] {
        for j := range strs {
            if i >= len(strs[j]) {
                return strs[0][:i]
            }
			
            if strs[0][i] != strs[j][i] {
                return strs[0][:i]
            }
        }
    }
	
    return strs[0]
}
```
Пример решения (№3) O(n):
```
Также кадидат может предложить решение с помощью trie (префиксного дерева), 
это оптимальное по времение решение за O(n), но долгое в реализации.
В таком случае, следует предложить кандидату решить задачу менее оптимальным, но более простым способом.
```

3) Задача "Пересечение двух массивов"

https://leetcode.com/problems/intersection-of-two-arrays/description/
```
Даны два целочисленных массива nums1 и nums2, верните массив их пересечения. 
Каждый элемент в результате должен быть уникальным, и вы можете вернуть результат в любом порядке.
Требуется наилучшее решение по времени выполнения.

Пример 1
Ввод: nums1 = [1,2,2,1], nums2 = [2,2]
Вывод: [2]

Пример 2
Ввод: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Вывод: [9,4]
```
```go
func intersection(nums1 []int, nums2 []int) []int {

}
``` 

Пример решения (№1) O(n):
```go
func intersection(nums1 []int, nums2 []int) []int {
    count:=make(map[int]bool)
    result:=make([]int, 0)
    
    for _,num := range nums1{
        count[num]=true
    }
    
    for _, num := range nums2{
        if count[num] {
            result=append(result,num)
            count[num]=false
        }
    }

    return result    
}
```

### Практические задачи (concurrency):
1) Задача "Асинхронное слияние каналов"

Реализовать функцию asyncMerge, которая будет производить асинхронное слияние каналов.

Исходные данные:
```go
func main(){
ch1 := make(chan int, 10)
ch2 := make(chan int, 20)

    ch1 <- 1
    ch2 <- 2
    ch2 <- 4
    
    close(ch1)
    close(ch2)
    
    ch3 := asyncMerge[int](ch1, ch2)
    
    for val := range ch3 {
        fmt.Println(val)
    }
}

func asyncMerge[T any](chans ...chan T)chan T {
    return nil
}
```

Пример решения:
```go
func asyncMerge[T any](chans ...chan T) chan T {
	result := make(chan T)
	wg := new(sync.WaitGroup)

	for _, singleChan := range chans {
		wg.Add(1)
		singleChan := singleChan

		go func() {
			defer wg.Done()

			for val := range singleChan {
				result <- val
			}
		}()
	}

	go func() {
		wg.Wait()
		close(result)
	}()

	return result
}
```

2) Задача "Конкурентный подсчет слов"

Реализовать асинхронный подсчет количества слов во всех файлах.

На вход получаем массив строк, который содержит названия файлов. Каждый файл содержит простой текст, где слова разделены пробелами.

Ожидаемый вывод: "total words: 15".

Исходные данные:

```go
func main(){
    files = []string{"file1.txt", "file2.txt", "file3.txt"}
}
```

Пример решения:
```go
// countWords reads a file and returns the number of words.
func countWords(filename string, wg *sync.WaitGroup, ch chan int) {
	defer wg.Done()

	fileContent, err := ioutil.ReadFile(filename)
	if err != nil {
		fmt.Printf("Error reading file %s: %v\n", filename, err)
		ch <- 0
		return
	}

	words := strings.Fields(string(fileContent))
	ch <- len(words)
}

func main() {
	files := []string{"file1.txt", "file2.txt", "file3.txt"}

	var wg sync.WaitGroup
	wordCountCh := make(chan int, len(files))

	for _, file := range files {
		wg.Add(1)
		go countWords(file, &wg, wordCountCh)
	}

	go func() {
		wg.Wait()
		close(wordCountCh)
	}()

	totalWords := 0
	for count := range wordCountCh {
		totalWords += count
	}

	fmt.Printf("Total words: %d\n", totalWords)
}
```

### Чтение кода:
Задача №1 [slice]

Условие:
```go
func main() {
    a := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
    s := a[2:5] // s = ...                        
    s2 := s[5:7] // s2 = ...

    s2 = append(s2, 11) // s2 = ...
    s2 = append(s2, 12) // s2 = ...

    fmt.Println(a) // a = ...
}
```

Ответ:
```go
func main() {
    a := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10} // len: 10, cap: 10
    s := a[2:5]                               // s = [3 4 5] len: 3, cap: 8
    s2 := s[5:7]                              // s2 = [8 9] len: 2, cap: 3

    s2 = append(s2, 11) // s2 = [8 9 11] len: 3, cap: 3
    s2 = append(s2, 12) // s2 = [8 9 11 12] len: 4, cap: 6

    fmt.Println(a) // a = [1 2 3 4 5 6 7 8 9 11]
}
```

Задача №2 [map]
```go
func main() {
    m := map[string]uint32{"milk": 90, "eggs": 100}

    for i := 0; i < 2; i++ {
        for _, value := range m {
            fmt.Println(value) // ...
        }
    }
    fmt.Println(m) // ...

    atomic.AddUint32(&m["milk"], 20) // ...

    fmt.Println(m) // ...

    mm := make(map[string]int, 4)
}
```

Ответ:
```go
func main() {
    m := map[string]uint32{"milk": 90, "eggs": 100}

    for i := 0; i < 2; i++ {
        for _, value := range m {
            // Порядок случайный. Внутри map есть функция, которая перемешивает значения.
            fmt.Println(value) // 90 100 90 100 || 90 100 100 90 || 100 90 90 100 || 100 90 100 90
        }
    }
    // Внутри функции fmt.Println происходит сортировка map по ключу.
    fmt.Println(m) // map[eggs:100 milk:90]

    // Нельзя взять указатель на элемент map. Это связано с эвакуацией.
    atomic.AddUint32(&m["milk"], 20) // ошибка компиляции

    fmt.Println(m) // Недостижимый код из-за ошибки компиляции
}
```

