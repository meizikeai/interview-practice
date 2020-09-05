## Interview Practice

记录一些面试题目，方便回看~ 脚下的路还很长，活着就要坚决走下去...

**1、排序**

``` js
/**
 * 冒泡排序
 * 1. 首先将所有待排序的数字放入工作列表中。
 * 2. 从列表的第一个数字到倒数第二个数字，逐个检查：若某一位上的数字大于他的下一位，则将它与它的下一位交换。
 * 3. 重复2号步骤(倒数的数字加1。例如：第一次到倒数第二个数字，第二次到倒数第三个数字，依此类推...)，直至再也不能交换。
 * @method bubbleSort
 * @param {Array} array
 */
function bubbleSort(array) {
    if (Object.prototype.toString.call(array) !== '[object Array]') {
        return array;
    }
    var count = array.length - 1;
    for (var i = 0; i < count; i++) {
        for (var j = 0; j < count - i; j++) {
            if (array[j] > array[j + 1]) {
                var temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
    return array;
}
console.log('冒泡排序：', bubbleSort([0, 1, 2, 44, 42, 43, 5, 1, 4, 51, 56, 76, 7, 7, 2, 1, 45, 4, 6, 7]));
```

``` js
function bubble(array) {
    if (Object.prototype.toString.call(array) !== '[object Array]') {
        return array;
    }
    var i = array.length - 1; //初始时,最后位置保持不变
    while (i > 0) {
        var pass = 0; //每趟开始时,无记录交换  
        for (var j = 0; j < i; j++) {
            if (array[j] > array[j + 1]) {
                pass = j; //记录交换的位置   
                var temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
        i = pass; //为下一趟排序作准备  
    }
    return array;
}
console.log('冒泡排序：', bubble([0, 1, 2, 44, 42, 43, 5, 1, 4, 51, 56, 76, 7, 7, 2, 1, 45, 4, 6, 7]));
```

``` js
/**
 * 排序算法 - 冒泡排序
 * @method bubbleSort1
 * @param {Array} arr 
 */
function bubbleSort1(arr) {
    for (var i = 0, l = arr.length; i < l - 1; i++) {
        for (var j = i + 1; j < l; j++) {
            if (arr[i] > arr[j]) {
                var temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
console.log(bubbleSort1([2, 4, 5, 63, 4, 5, 63, 2, 4, 43]));
```

``` js
/**
 * 排序算法 - 插入排序
 * 1. 从第一个元素开始，认为该元素已经是排好序的。
 * 2. 取下一个元素，在已经排好序的元素序列中从后向前扫描。
 * 3. 如果已经排好序的序列中元素大于新元素，则将该元素往右移动一个位置。
 * 4. 重复步骤3，直到已排好序的元素小于或等于新元素。
 * 5. 在当前位置插入新元素。
 * 6. 重复步骤2。
 * @method insertionSort
 * @param {Array} array
 */
function insertionSort(array) {
    if (Object.prototype.toString.call(array) !== '[object Array]') {
        return array;
    }
    var count = array.length;
    for (var i = 1; i < count; i++) {
        var temp = array[i];
        for (var j = i; j > 0 && array[j - 1] > temp; j--) {
            array[j] = array[j - 1];
        }
        array[j] = temp;
    }
    return array;
}
console.log('插入排序：', insertionSort([0, 1, 2, 44, 42, 43, 5, 1, 4, 51, 56, 76, 7, 7, 2, 1, 45, 4, 6, 7]));
```

``` js
/**
 * 排序算法 - 播入排序
 * @method insertSort
 * @param {Array} arr 
 */
function insertSort(arr) {
    var min;
    var temp;
    for (var i = 1; i < arr.length; i++) {
        min = i;
        temp = arr[min];
        while (--min > -1) {
            if (arr[min] > temp) {
                arr[min + 1] = arr[min];
            } else {
                break;
            }
        }
        arr[min + 1] = temp;
    }
    return arr;
}
console.log(insertSort([2, 4, 5, 63, 4, 5, 63, 2, 4, 43]));
```

``` js
/**
 * 排序算法 - 选择排序
 * 1. 设数组内存放了n个待排数字，数组下标从1开始，到n结束。
 * 2. i=1
 * 3. 从数组的第i个元素开始到第n个元素，寻找最小的元素。（具体过程为:先设arr[i]为最小，逐一比较，若遇到比之小的则交换）
 * 4. 将上一步找到的最小元素和第i位元素交换。
 * 5. 如果i=n－1算法结束，否则回到第3步
 * @method selectionSort
 * @param {Array} array
 */
function selectionSort(array) {
    if (Array.isArray(array)) {
        var count = array.length;
        for (var i = 0; i < count - 1; i++) {
            var key = i;
            for (var j = i + 1; j < count; j++) {
                if (array[j] < array[key]) {
                    key = j;
                }
            }
            var temp = array[i];
            array[i] = array[key];
            array[key] = temp;
        }
    }
    return array;
}
console.log('选择排序：', selectionSort([0, 1, 2, 44, 42, 43, 5, 1, 4, 51, 56, 76, 7, 7, 2, 1, 45, 4, 6, 7]));
```

``` js
/**
 * 排序算法 - 选择排序
 * @method selectionSort1
 * @param {Array} arr 
 */
function selectionSort1(arr) {
    var min, temp;
    for (var i = 0; i < arr.length - 1; i++) {
        min = i;
        for (var j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[min]) {
                min = j;
            }
        }
        temp = arr[i];
        arr[i] = arr[min];
        arr[min] = temp;
    }
    return arr;
}
console.log(selectionSort1([2, 4, 5, 63, 4, 5, 63, 2, 4, 43]));
```

``` js 
/**
 * 排序算法 - 快速排序
 * 快速排序是所有排序算法中最高效的一种。它采用了分治的思想：先保证列表的前半部分都小于后半部分，然后分别对前半部分和后半部分排序，这样整个列表就有序了。
 * 快速排序的基本算法是：
 * 1. 从数列中挑出一个元素，称为 "基准"（pivot），
 * 2. 重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分割之后，该基准是它的最后位置。这个称为分割（partition）操作。
 * 3. 递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序。
 * 递回的最底部情形，是数列的大小是零或一，也就是永远都已经被排序好了。虽然一直递回下去，但是这个算法总会结束，因为在每次的迭代（iteration）中，它至少会把一个元素摆到它最后的位置去。
 * @method quickSort
 * @param {Array} array
 */
function quickSort(array) {

    if (!Array.isArray(array)) {
        return array;
    }

    var i = 0;
    var j = array.length - 1;

    var sort = function (i, j) {
        if (i == j) {
            return;
        }

        var key = array[i];
        var start = i; // 记录开始位置
        var end = j;   // 记录结束位置

        while (j > i) { // j <<-------------- 向前查找
            if (array[j] >= key) {
                j--;
            } else {
                array[i] = array[j];

                while (j > ++i) { //i++ ------------>>向后查找
                    if (array[i] > key) {
                        array[j] = array[i];
                        break;
                    }
                }
            }
        }

        // 如果第一个取出的 key 是最小的数
        if (start == i) {
            sort(++i, end);
            return;
        }

        // 最后一个空位留给 key
        array[i] = key;

        // 递归
        sort(start, i);
        sort(j, end);
    }

    sort(i, j);

    return array;

}
console.log('快速排序：', quickSort([0, 1, 2, 44, 42, 43, 5, 1, 4, 51, 56, 76, 7, 7, 2, 1, 45, 4, 6, 7])); 

``` 
``` js
/**
 * 排序算法 - 快速排序
 * @method quickSort1
 * @param {Array} arr 
 */
function quickSort1(arr) {
    var result = [];

    if (typeof arr !== 'object') {
        result = null;
    } else {

        if (arr.length > 0) {
            var pivot = arr[0];
            var left = [];
            var right = [];

            for (var i = 1; i < arr.length; i++) {
                if (arr[i] < pivot) {
                    left.push(arr[i]);
                } else {
                    right.push(arr[i]);
                }
            }

            console.log('left:' + left);
            console.log('right:' + right);

            result = quickSort1(left).concat(pivot, quickSort1(right));

            console.log('result:' + result);
        } else {
            result = arr;
        }
    }

    return result;
}
console.log(quickSort1([15, 2, 4, 5, 63, 4, 5, 63, 2, 4, 43]));
```

``` js
/**
 * 排序算法 - 希尔排序
 * 先取一个正整数 d1(d1 < n)，把全部记录分成 d1 个组，所有距离为 d1 的倍数的记录看成一组，然后在各组内进行插入排序
 * 然后取 d2(d2 < d1)
 * 重复上述分组和排序操作；直到取 di = 1(i >= 1) 位置，即所有记录成为一个组，最后对这个组进行插入排序。一般选 d1 约为 n/2，d2 为 d1 /2， d3 为 d2/2 ，…， di = 1。
 * @method shellSort
 * @param {Array} array
 */
function shellSort(array) {
    if (!Array.isArray(array)) {
        return array;
    }

    function swap(array, i, k) {
        var temp = array[i];
        array[i] = array[k];
        array[k] = temp;
    }

    var length = array.length;
    var gap = Math.floor(length / 2);

    while (gap > 0) {
        for (var i = gap; i < length; i++) {
            for (var j = i; 0 < j; j -= gap) {
                if (array[j - gap] > array[j]) {
                    swap(array, j - gap, j);
                } else {
                    break;
                }
            }
        }
        gap = Math.floor(gap / 2);
    }

    return array;
}
console.log('希尔排序：', shellSort([0, 1, 2, 44, 42, 43, 5, 1, 4, 51, 56, 76, 7, 7, 2, 1, 45, 4, 6, 7]));
```

``` js
/**
 * 排序算法 - 利用数组的sort方法进行排序
 * @method systemSort
 * @param {Array} array 
 */
function systemSort(array) {
    return array.sort(function(a, b) {
        return a - b;
    });
}
console.log(systemSort([3, '4', 1, 2]));
```

``` js
/**
 *  排序算法 - setTimeout实现最慢的数组排序
 * 比如：[5, 10, 1, 32, 80, 50, 100] => 
 * @method longTimeSort
 * @param {Array} array 
 */
function longTimeSort(array) {
    var sort = [];

    array.forEach(a => {
        setTimeout(() => {
            sort.push(a);
        }, a);
    });

    return sort;
}
console.log(longTimeSort([5, 10, 1, 32, 80, 50, 100]));
```

**2、实现一个算法，随机生成指制定长度（从26个字母+10个数字中取）的字符窜~**

``` js
/**
 * 实现一个算法，随机生成指制定长度（从26个字母+10个数字中取）的字符窜~
 * @method randomString
 * @param {Number} count
 */
function randomString(count) {
    var string = 'abcdefghijklmnopqrstuvwxyz0123456789';
    var temp = "";
    var key = string.length;

    for (var i = 0; i < count; i++) {
        temp += string.charAt(Math.floor(Math.random() * key));
    }

    return temp;
}
console.log(randomString(8));
```

``` js
function randomString1(len) {
    var result = '';
    while (len--) {
        result += String.fromCharCode(~~(Math.random() * 2) === 1 ? (Math.random() * 10 + 48) : Math.random() * 26 + 97);
    }
    return result;
}
console.log(randomString1(10));
```

``` js
function randomString2(length) {
    var result = Math.random().toString(36).slice(2);
    while (result.length < length) {
        result += Math.random().toString(36).slice(2);
    }
    return result.slice(-length);
}
```

``` js
function randomString3(long) {
    var result = '';
    for (var i = 0; i < long; i++) {
        result += String.fromCharCode(97 + Math.ceil(Math.random() * 26));
    }
    return result;
}
console.log(randomString3(6));
```

**3、在传入的数中（脚本可选的数）找出最大的连续的五位数并返回~**

``` 
/**
 * 返回一个数中最大的连续五位数
 * @param {Number} number
 * findMaxNumber(123456) => 23456
 * return Number
 */
function findMaxNumber(number) {
    var string = number + '';

    if (string.length <= 5) {
        return number;
    }

    var total = string.length - 5;
    var result = null;

    for (var i = 0; i <= total; i++) {
        var max = string.substring(i, i + 5);
        if (result < max) {
            result = max;
        }
    }

    return result;
}
console.log(findMaxNumber(123456));
```

``` js
function getMax(num) {
    num = String(num);
    var arrNum = Array.from(num);
    var length = num.length;
    var i, arr = [];
    for (i = 0; i < length - 4; i++) {
        arr.push(arrNum.slice(-5).join(''));
        arrNum.splice(-1, 1);
    }

    return Math.max(...arr);
}
console.log(getMax(123456789));
```

**4、由短链接引发的ip转为整数，反之**

``` js
/**
 * ip比如 192.168.1.1，转为二进制后是 192: 11000000 、168: 10101000 、1: 00000001 、1: 00000001，
 * 串起来是 10000000001000000000101000000001 ，转十进制就是 3232235777 
 * 把 3232235777 转回 IP
 * @param {Number} int32 
 */
function intToIp(number) {
    return number.toString(2).match(/\d{8}/gi).map(function(value, key) {
        return parseInt(value, 2);
    }).join('.');
}
console.log(intToIp(3232235777)); //< "192.168.1.1"
```

``` js
/**
 * 把ip转换成二进制后、串成字符串，再转成十进制
 * 192.168.1.1 => 10000000001000000000101000000001 => 3232235777
 * @param {String} string 
 */
function ipToInt(string) {
    var temp = string.split('.');
    var fillZero = function(str) {
        if (str.length < 9) {
            return new Array(9 - str.length).join('0') + str;
        }
        return str;
    };
    var result = '';

    if (temp.length === 4) {
        temp.map(function(value, key) {
            result += fillZero(parseInt(value).toString(2));
        });
    }

    return parseInt(result, 2);
}
```

``` js
// 学霸
function ip2int(ip) {
    return parseInt(ip.split('.').reduce((str, item) => str += (~~item).toString(2).padStart(8, '0'), ''), 2)
}
// 学霸
function int2ip(int) {
    return (int).toString(2).match(/\d{8}/g).map(item => parseInt(item, 2)).join('.');
}
```

``` js
// 车车
function ipToInt2(ip) {
    return parseInt(ip.replace(/(\d)*\D+|(\d)*$/g, function(a) {
        return ('00000000' + (+a).toString(2)).slice(-8)
    }), 2)
}
```

**5、对对象进行排序**

``` js
//原始数据
// [{ "name": "zzz", "age": 12, "sex": 1 }, { "name": "zzz", "age": 12, "sex": 0 }, { "name": "aaa", "age": 12, "sex": 1 }, { "name": "bbb", "age": 14, "sex": 1 }, { "name": "zzz", "age": 14, "sex": 1 }, { "name": "bbb", "age": 12, "sex": 0 }, { "name": "sdf", "age": 12, "sex": 0 }, { "name": "sd", "age": 12, "sex": 1 }, { "name": "sdf", "age": 15, "sex": 0 }, { "name": "sdf", "age": 15, "sex": 1 }, { "name": "sdf", "age": 12, "sex": 1 }]
```

``` js
//最终数据
// [{ "name": "aaa", "age": 12, "sex": 1 }, { "name": "bbb", "age": 12, "sex": 0 }, { "name": "bbb", "age": 14, "sex": 1 }, { "name": "sd", "age": 12, "sex": 1 }, { "name": "sdf", "age": 12, "sex": 1 }, { "name": "sdf", "age": 12, "sex": 0 }, { "name": "sdf", "age": 15, "sex": 1 }, { "name": "sdf", "age": 15, "sex": 0 }, { "name": "zzz", "age": 12, "sex": 1 }, { "name": "zzz", "age": 12, "sex": 0 }, { "name": "zzz", "age": 14, "sex": 1 }]
```

解决方法：

* https://www.npmjs.com/package/sort-fn
* https://github.com/Jiasm/notebook/blob/master/sort.js

**6、一个实现 1234567 =》1, 234, 567 的写法~**

``` js
/**
 * 将 12345678 转化成：12,345,678
 * @param {Number/String} data
 * '1234567'.replace(/([0-9])(?=([0-9]{3})+$)/g,'$1,')
 */
function formatRMB(data) {
    return data.toString().replace(/(?=(\d{3})+(\.))/g, ',');
    // return data.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    // return data.toString().split('').reverse().join('').match(/\d{3}|\d{2}|\d{1}|/gi).join(',').split('').reverse().join('').substring(1);
}
```

**7、先解释浅克隆、深度克隆，然后写实现一个深度克隆？一个保留对象的地址引用，一个不保留**

``` js
/**
 * 写一个函数，实现深度克隆
 * @param {Object} obj 
 */
function cloneSame(obj) {
    var str = '';
    var news = obj.constructor === Array ? [] : {};

    if (typeof obj !== 'object') {
        return null;
    } else if (JSON) {
        str = JSON.stringify(obj);
        news = JSON.parse(str);
    } else {
        for (var i in obj) {
            news[i] = typeof obj[i] === 'object' ? cloneSame(obj[i]) : obj[i];
        }
    }
}
```

**8、匹配字符，第一个必须是字母或下划线开头，长度5-10**

``` js
/**
 * 匹配字符，第一个字符必须是字母或下划线，长度5-10
 * @param {String} string 
 */
function testString(string) {
    return /^[a-zA-Z_]{1}[a-zA-Z0-9_]{4,9}/.test(string);
    // /^(_|[a-zA-Z]{1})[\w\W]{4,9}$/
    // /^[_a-zA-Z].{4,9}$/
}
```

**9、写一个toRGB函数，处理颜色编码~ **

``` js
/**
 * 写一个toRGB函数，处理颜色编码~ 
 * 要求：1、#0000FF => rgb(0, 0, 255) 2、red => red 3、#G00 => #G00
 * 参考：https://github.com/Jiasm/notebook/blob/master/colorChanger.html
 * @param {String} input 
 */
var toRGB = function(input) {
    var result = input;
    var list = [];
    var pattern = [
        /[0-9a-f]{1}/ig,
        /[0-9a-f]{2}/ig
    ];
    var index = 0;
    if (/^#([0-9a-f]{3}|[0-9a-f]{6})$/i.test(input)) {
        index = (input.length - 1) / 3 - 1;
        input.match(pattern[index]).forEach(function(item) {
            list.push(parseInt(item.repeat(2).slice(-2), 16));
        })
        result = 'rgb(' + list.join(', ') + ')'
    }
    return result;
};

var toRGBtwo = function(str) {
    return str.replace(/#(([0-9a-f]{6})|([0-9a-f]{3}))$/ig, ($, $1, $2, $3) => {
        return $2 ? `rgb(${$2.match(/.{2}/g).map(item => parseInt(item, 16)).join(',')})` :
 `rgb(${$3.match(/./g).map(item => parseInt(item.repeat(2), 16)).join(',')})`
    })
}
```

**10、Array上有个reverse()方法。现请在String上实现下，实现方式不限？**

``` js
/**
 * 在String对象的原型上创建一个方法，实现以下功能
 * "String".reverse() // return "gnirtS"
 */
String.prototype.reverse = function() {
    return this.split('').reverse().join('');
};
// console.log("asdf".reverse() === "fdsa");
```

**11、写一个方法，用于确定传递的值是否是一个Array[不能使用Array.isArray()]，返回Boolean。**

``` js
/**
 * 写一个方法，用于确定传递的值是否是一个Array[不能使用Array.isArray()]，返回Boolean。
 * http://www.cnblogs.com/winter-cn/archive/2009/12/07/1618281.html
 * https://github.com/Precursors/Detection
 * 很多时候咱们都需要对一些参数进行判断，判断它到底是否符合要求~
 * 例如：Array.isArray()这样的。
 * 那么问题来了，在没提供现有方法的情况下，请写一个isArray(obj)的方法，返回boolean。
 * 扩展，列举你知道的其它判断方式~其它类型的种类？
 * @param {String} obj 
 */
function isArray(obj) {
    return Object.prototype.toString.call(obj) === '[object Array]';
}
// console.log(isArray([]));
```

**12、对Array.reverse()方法的重写。为什么不要改变原方案？**

``` js
/**
 * 对Array.reverse()方法的重写。为什么不要改变原方案？
 * [1,2,3].reverse() // return "[3,2,1]"
 * return this
 */
Array.prototype.reverse = function() {
    for (var i = 0; i < this.length / 2; i++) {
        var temp = this[i];
        var index = this.length - 1 - i;

        this[i] = this[index];
        this[index] = temp;
    }
    return this;
};
// console.log([1, 2, 3].reverse());
```

**13、判断传入的参数是否为素数（质数），返回true 或 false。**

``` js
/**
 * 判断传入的参数是否为素数（质数），返回true 或 false。
 * @param {Number} n 
 * return {Boolean}
 */
function isPrime(n) {
    var number = parseFloat(n);

    if (number <= 0 || number == 1) {
        return false;
    }

    if (number == 2 || number == 3) {
        return true;
    }

    for (var i = 2; i <= number / 2 + 1; i++) {
        if (number % i === 0) {
            return false;
        } else {
            return true;
        }
    }
}
```

``` js
function isPrime(n) {
    if (n <= 3) {
        return n > 1;
    }
    if (n % 2 == 0 || n % 3 == 0) {
        return false;
    }

    for (var i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) {
            return false;
        }
    }

    return true;
}
```

``` js
//请做以下测试
// console.log(isPrime(0)); // => false
// console.log(isPrime(1)) // => false
// console.log(isPrime(2)) // => true
// console.log(isPrime(3)) // => true
// console.log(isPrime(4)) // => false
// console.log(isPrime(157)) // => true
```

**14、写一个最简版的ajax函数**

``` js
/**
 * 使用原生封装一个最简版的ajax函数（不用考虑兼容）
 */
function setAjax(obj) {
    var fn = obj.callback || function() {};
    var type = obj.type || "get";
    var url = obj.url || "";

    var xmlhttp = new XMLHttpRequest();

    xmlhttp.open('get', url, true); //false同步，true异步
    xmlhttp.onreadystatechange = function() {
        if (xmlhttp.readyState == 4) {
            if (xmlhttp.status == 200) {
                console.log(xmlhttp.responseText);
            }
        }
    };
    xmlhttp.send();
}

var ajax = function(option) {
    var xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function() {
        var data;
        if (xhr.readyState === 4 && xhr.status === 200) {
            data = JSON.parse(xhr.responseText);
            option.callback(data);
        }
    };
    if (option.type.toLowerCase() === 'get') {
        xhr.open('get', option.url + JSON.stringify(option.data), true);
        xhr.send();
    } else {
        xhr.open('post', option.url, true);
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
        xhr.send(JSON.stringify(option.data));
    }
}
```

**15、数组去重，简述你知道的方式~**

``` js
/*
 * 数组去重方案 - indexOf
 * @param {arrs} 原数组
 * @method 新建一个新数组，遍历原数组，在新数组内使用indexOf查找原数组内的每一项，如果没有找到，就把当前的项存入新数组里面去，这样就过滤掉
 * 重复项 indexOf方法在IE8及IE8以下不支持
 * @return {newArrays} 返回新数组
 */
function arrayUnique(arr) {
    var temp = [];

    if (typeof arr === 'object' && arr.constructor === Array) {
        for (var i = 0; i < arr.length; i++) {
            if (temp.indexOf(arr[i]) < 0) {
                temp.push(arr[i]);
            }
        }
    }

    return temp;
}
console.log(arrayUnique([2, 4, 5, 63, null, 5, 63, 2, 4, 43]));
```

``` js
/*
 * 数组去重方案 - 排序后相邻去除法
 * @method 新建一个新数组，遍历当前的数组，如果当前的数组某一项不等于新数组的最后一项的话，就把当前的项存入新数组中，最后返回新数组
 */
function arrayUnique1(arr) {
    var temp = [];

    if (typeof arr === 'object' && arr.constructor === Array) {
        arr.sort();
        for (var i = 0; i < arr.length; i++) {
            if (arr[i] !== temp[temp.length - 1]) {
                temp.push(arr[i]);
            }
        }
    }

    return temp;
}
console.log(arrayUnique1([2, 4, 5, 63, null, 5, 63, 2, 4, 43]));
```

``` js
/*
 * 数组去重方案 - 对象键值法(该方法性能最优)
 * @method 定义一个空对象和空新数组，遍历当前的数组，判断该对象是否存在数组的某一项，如果不存在
 * 就当当前的某一项存入新数组去，且当前的项置为-1 目的过滤掉重复的项
 */
function arrayUnique2(arr) {
    var temp = [];
    var hash = {};

    if (typeof arr === 'object' && arr.constructor === Array) {
        for (var i = 0; i < arr.length; i++) {
            if (!hash[arr[i]]) {
                hash[arr[i]] = true;
                temp.push(arr[i]);
            }
        }
    }

    return temp;
}
console.log(arrayUnique2([2, 4, 5, 63, null, 5, 63, 2, 4, 43]));
```

``` js
/*
 * 数组去重方案 - new Set();
 * @method es6的方案
 */

function arrayUnique3(arr) {
    return [...new Set(arr)];
}
console.log(arrayUnique3([2, 4, 5, 63, null, 5, 63, 2, 4, 43]));
```

**16、请简述实现倒计时方案（你的），要求精准度！**

``` js
/**
 * https://www.xuanfengge.com/js-realizes-precise-countdown.html
 * 1. 要了解好js单线程工作原理；
 * 2. 清楚了解服务器系统时间传送到前端的流程；
 * 3. 了解前端渲染和线程阻塞造成的时间误差；
 */
```

**17、请实现9*9乘法表**

``` js
(function multiplication(l, i) {
    var temp = [];
    while (i <= l) {
        temp.push([i, '*', l, '=', i * l].join(''));
        i += 1;
    }
    console.log(temp.join(' '));
    if (l < 9) {
        l += 1;
        multiplication(l, 1);
    }
}(1, 1));

function multiplication2() {
    return [1, 2, 3, 4, 5, 6, 7, 8, 9].map(function(e) {
        var array = Array.from({
            length: e
        });
        return array.map(function(_e, i) {
            return `${e} * ${i + 1} = ${e * (i + 1)}` ; //template string
        }).join('  ');
    }).join('\n');
}
console.log(multiplication2());

function multiplication3() {
    return [1, 2, 3, 4, 5, 6, 7, 8, 9].map(e => Array.from({
        length: e
    }).map((_e, i) => `${e} * ${i + 1} = ${e * (i + 1)}` ).join('  ')).join('\n');
}
console.log(multiplication3());
```

**18、写一个函数，查找对象某个属性最大与最小值，例如price**

``` js
/**
 * 写一个函数，查找对象某个属性最大与最小值，例如price
 * @param {Object} obj 
 */
function maxAndmin(attr, obj) {
    var result = {
        max: '',
        min: ''
    };
    var temp = []; //存放所有price
    var pass = obj.constructor === Array; //确定传参一定为数据

    if (pass && obj.length > 0) { //为数组、并且有一条数据时

        for (var i = 0; i < obj.length; i++) {
            if (obj[i][attr]) {
                temp.push(obj[i][attr]);
            }
        }

        if (obj.length == 1) { //有且只有一条
            result.max = result.min = obj[0][attr];
        } else {
            result.max = Math.max.apply(null, temp);
            result.min = Math.min.apply(null, temp);
        }
    }

    return result;
}
var priceValue = maxAndmin('price', [{
    "price": "6800"
}, {
    "price": "7800"
}, {
    "price": "8800"
}, {
    "price": "9800"
}, {
    "price": "11800"
}, {
    "price": "13800"
}]);

console.log(priceValue.min, priceValue.max);

var [biggest, b] = Object.values({
    a: 1,
    b: 3,
    c: 12,
    d: 8
}).sort((a, b) => b - a);

console.log([biggest, b]);
```

**19、利用数组的方法，把[1, 2, 3, 4, 5]变成[1, 2, 3, 4, 5, 4, 3, 2, 1]**

``` js
/**
 * 利用数组的方法，把[1, 2, 3, 4, 5]变成[1, 2, 3, 4, 5, 4, 3, 2, 1]
 * @param {Array} array 
 */
function arrayReverse(array) {
    // return array.concat(([].concat(array).reverse().slice(1)));
    return array.slice(0).concat(array.reverse().slice(1));
}
console.log(arrayReverse([1, 2, 3, 4, 5]));
```

**20、判断两个字符串是不是回文**

``` js
/**
 * 判断两个字符串是不是回文
 * @param {String} a 
 * @param {String} b 
 */
function isMathOne(a, b) {
    return a === b.split('').reverse().join('');
}
console.log(isMathOne('1224444', '0987654321'));
```

``` js
/**
 * 判断两个字符串是不是回文
 * @param {String} a 
 * @param {String} b 
 */
function isMathTwo(a, b) {
    var onelen = a.length;
    var twolen = b.length;

    if (onelen !== twolen) {
        return false;
    } else {
        for (var i = 0, j = twolen - 1; i < onelen; i++, j--) {
            if (a[i] !== b[j]) {
                return false;
            }
        }
        return true;
    }
}
console.log(isMathOne('1234567890', '0987654321'));
```

``` js
/**
 * 判断一个单词是否是回文
 * @param {String} str 
 */
function checkPalindrom(str) {
    return str === str.split('').reverse().join('');
}
console.log(checkPalindrom('mom'));
```

**21、查找当前页面使用了多少种标签**

``` js
/**
 * 查找当前页面使用了多少种标签
 */
function querySelectDom() {
    var dom = document.querySelectorAll('*');
    var arr = Array.from(dom);
    arr = arr.map((value) => {
        return value.nodeName;
    });

    arr = new Set(arr);
    arr = Array.from(arr);

    return arr;
}
console.log(querySelectDom(), querySelectDom().length);
```

**22、实现一个斐波那契数列**

``` js
/**
 * 实现一个斐波那契数列
 * 根据传入的数值，返回一个等长的，斐波那契数列的数组。
 * 如果参数为负数，那么返回空数组
 * @param {Number} num
 */

function fibonacci(num) {
    var number = +num;
    if (number === 1) {
        return [0];
    }
    if (number === 2) {
        return [0, 1];
    }
    if (number > 2) {
        var result = fibonacci(number - 1);
        result[number - 1] = result[number - 2] + result[number - 3];
        return result;
    }
    return [];
}
console.log(fibonacci(4)); // should return [0,1,1,2]
console.log(fibonacci(-1)); // should return []
```

**23、写一个函数，实现concatAdd(1)(2)(3)返回6**

``` js
/**
 * 写一个函数，实现concatAdd(1)(2)(3)返回6
 * @param arguments
 */
function concatAdd() {
    var arg = [].slice.call(arguments);

    var fn = function() {
        var that = [].slice.call(arguments);
        return concatAdd.apply(null, arg.concat(that));
    };

    fn.toString = function() {
        return arg.reduce(function(a, b) {
            return a + b;
        });
    };

    return fn;
}
```

``` js
function concatAdd2(m) {
    var r = m;

    function p(n) {
        r += n;
        return p;
    }

    p.valueOf = function() {
        return r;
    }

    return p;
}
```

``` js
function concatAdd3(n) {
    function fn(m) {
        n += m;
        return fn;
    }

    fn.toString = fn.valueOf = function() {
        return n
    }

    return fn;
}
console.log(concatAdd(1)(2)(3));
```

**24、判断数组中是否有相同的元素**

``` js
/**
 * 判断数组中是否有相同的元素
 * -- 通过字符replace掉自己，再查找自已
 * @param {Array} arr 
 */
function isRepeatOne(arr) {
    if (arr.length > 0) {
        var str = arr.join('');
        for (var i = 0; i < str.length; i++) {
            str = str.replace(arr[i], '');
            if (str.indexOf(arr[i]) > 0) {
                return true;
            }
        }
    }
    return false;
}
console.log(isRepeatOne([1, 2, 3, 1, 2]));
```

``` js
/**
 * 判断数组中是否有相同的元素
 * -- 通过对象属性判断
 * @param {Array} arr 
 */
function isRepeatTwo(arr) {
    var hash = {};
    if (arr.length > 0) {
        for (var i = 0; i < arr.length; i++) {
            if (hash[arr[i]]) {
                return true;
            } else {
                hash[arr[i]] = true;
            }
        }
    }
    return false;
}
console.log(isRepeatTwo([1, 2, 3]));
```

**25、对给定的字符串或数组，算出每个元素在数组中出现的个数**

``` js
/**
 * 对给定的字符串或数组，算出每个元素在数组中出现的个数
 * @param [Array]
 */
function arrayElemCount(arr) {
    var newarr = {};

    if (typeof arr === 'string') {
        arr = arr.split('');
    }

    if (typeof arr === 'object' && arr.constructor === Array) {
        if (arr.length > 0) {
            for (var i = 0; i < arr.length; i++) {
                var temp = arr[i];
                var count = 0;

                for (var j = 0; j < arr.length; j++) {
                    if (arr[j] == temp) {
                        count++;
                    }
                }

                newarr[temp] = count;
            }
        }
    }

    return newarr;
}
console.log(arrayElemCount(['a', 'b', 'a', 'c']));
```

**26、接上例，找出数组中出现最多的个数及字符**

``` js
/**
 * 接上例，找出数组中出现最多的个数及字符
 * @param {Array} arr 
 */
function arrayElemMax(arr) {
    var result = arrayElemCount(arr); //可以自己写，不想重复
    var temp = [];

    for (var i in result) {
        if (result.hasOwnProperty(i)) {
            temp.push(result[i]);
        }
    }

    var max = Math.max.apply(null, temp);
    var str = [];

    for (var j in result) {
        if (result.hasOwnProperty(j)) {
            if (max == result[j]) {
                str.push(j);
            }
        }
    }

    return {
        count: max,
        string: str.join(',')
    };
}
console.log(arrayElemMax('afdsafdsafdfffsaffdaeerrtaaaert'));
```

**27、从一段英文字符串中，找出重复出现次数最多的字母及数量**

``` js
/**
 * 从一段英文字符串中，找出重复出现次数最多的字母及数量
 * 比如：who is your love? => o:3
 * @param {String} str
 */
function findMaxString(str) {
    if (!str || str.length == 1) {
        return str;
    }

    var temp = str.split('');
    var result = {};

    for (let i = 0; i < temp.length; i++) {
        if (result[temp[i]]) {
            result[temp[i]] += 1;
        } else {
            result[temp[i]] = 1;
        }
    }

    var max = Math.max.apply(null, Object.values(result));
    var key = '';

    for (let k in result) {
        if (result[k] == max) {
            key = k;
            break;
        }
    }

    return key + ':' + max;
}
console.log(findMaxString('who is your love?'));
```

``` js
/**
 * 统计一个字符串出现最多的字母
 * @param {String} str 
 */
function repeatCount(str) {
    var result = {};
    var tests = [];

    var maxChart = '';
    var maxCount = 0;

    if (str && typeof str !== "string") {
        result = 'str is not string';
    } else {

        tests = str.split("");

        for (var i = 0; i < tests.length; i++) {
            if (result[tests[i]]) {
                result[tests[i]] += 1;
            } else {
                result[tests[i]] = 1;
            }
        }

        //尝试使用Object.values处理对象
        // result = Object.values(result).sort(function(a, b) {
        //     return b - a;
        // })[0];

        for (var k in result) {
            if (result[k] > maxCount) {
                maxChart = k;
                maxCount = result[k];
            }
        }

        result = maxChart + ':' + maxCount;

    }

    return result;
}
console.log(repeatCount('jfdkafjdalfjdfkdjasfkjdasfkjsdadk'));
```

**28、找出数组中的最大差值**

``` js
/**
 * 找出数组中的最大差值
 * 比如：[8, 6, 10, 2, 3, 5] => 8
 * @param {Array} array
 */
function getMaxProfit(array) {
    var max = 0;
    var min = 0;

    if (Array.isArray(array)) {
        max = Math.max.apply(null, array);
        min = Math.min.apply(null, array);
    }

    return max - min;
}
console.log(getMaxProfit([8, 6, 10, 2, 3, 5]));
```

**29、根据传入的参数，返回在此参数之前的所有自然数是3或5的倍数的和**

``` js
/**
 * 根据传入的参数，返回在此参数之前的所有自然数是3或5的倍数的和
 * solution(10) //=> 3 + 5 + 6 + 9 = 23
 * @param {Number} num
 */
function solution(num) {
    var result = 0;
    for (var i = 0; i < num; i++) {
        if (i % 3 === 0 || i % 5 === 0) {
            result += i;
        }
    }
    return result;
}
console.log(solution(10));
```

**30、写一个函数来判断传入的两个数组是否相似，当以下全部满足，则返回true，否则返回false**

``` js
/**
 * 写一个函数来判断传入的两个数组是否相似，当以下全部满足，则返回true，否则返回false
 * 1、数组中的成员类型相同，顺序可以不同。例如[1, true] 与 [false, 2]是相似的。
 * 2、数组的长度一致。
 * 3、类型的判断范围，需要区分:String, Boolean, Number, undefined, null, 函数，日期, window。
 * @param {Array} arrOne 
 * @param {Array} arrTwo 
 */
function arraysSimilar(arrOne, arrTwo) {
    if (!(arrOne instanceof Array) || !(arrTwo instanceof Array)) {
        return false;
    }

    if (arrOne && arrOne.length !== arrTwo && arrTwo.length) {
        return false;
    }

    var count = arrOne.length;
    var mapOne = {};
    var mapTwo = {};
    var types = ["string", "boolean", "null", "undefined", "number", "function", "array", "date", "window"];

    function typeOf(ele) {
        var result = '';

        if (ele === null) {
            result = "null";
        } else if (ele instanceof Array) {
            result = "array";
        } else if (ele === window) {
            result = "window";
        } else if (ele instanceof Date) {
            result = "date";
        } else {
            result = typeof ele;
        }

        return result;
    }

    for (var i = 0; i < count; i++) {
        var key = typeOf(arrOne[i]);
        var index = typeOf(arrTwo[i]);

        if (mapOne[key]) {
            mapOne[key]++;
        } else {
            mapOne[key] = 1;
        }

        if (mapTwo[index]) {
            mapTwo[index]++;
        } else {
            mapTwo[index] = 1;
        }
    }

    console.log(mapOne);
    console.log(mapTwo);

    for (var j = 0; j < types.length; j++) {
        if (mapOne[types[j]] !== mapTwo[types[j]]) {
            return false;
        }
    }

    return true;
}
```

``` js
// 执行以下代码得到判断结果
var result = function() {
    var cases = [
        // case 1, 基本case
        {
            arr1: [1, true, null],
            arr2: [null, false, 100],
            expect: true
        },
        // case2, function区分
        {
            arr1: [function() {}, 100],
            arr2: [100, {}],
            expect: false
        },
        // case3, null区分
        {
            arr1: [null, 999],
            arr2: [{}, 444],
            expect: false
        },
        // case4, 应该相等的全类型乱序case
        {
            arr1: [window, 1, true, new Date(), "hahaha", (function() {}), undefined],
            arr2: [undefined, (function() {}), "okokok", new Date(), false, 2, window],
            expect: true
        },
        // case5, Date()区分
        {
            arr1: [new Date()],
            arr2: [{}],
            expect: false
        },
        // case6, window区分
        {
            arr1: [window],
            arr2: [{}],
            expect: false
        },
        // case7, undefined / null 区分
        {
            arr1: [undefined, 1],
            arr2: [null, 2],
            expect: false
        },
        // case8, 奇葩case
        {
            arr1: [new Object, new Object, new Object],
            arr2: [{}, {}, null],
            expect: false
        },
        // case9, 边界1
        {
            arr1: null,
            arr2: null,
            expect: false
        },
        // case10, 边界2
        {
            arr1: [],
            arr2: undefined,
            expect: false
        },
        // case11, 边界3
        {
            arr1: "abc",
            arr2: "cba",
            expect: false
        }
    ];

    for (var i = 0; i < cases.length; i++) {
        if (arraysSimilar(cases[i].arr1, cases[i].arr2) !== cases[i].expect) {
            // console.error('不通过！case' + (i + 1) + '不正确！arr1:' + cases[i].arr1.toString() + ', arr2:' + cases[i].arr2.toString() + ' 的结果不是' + cases[i].expect);
            return false;
        }
    }

    return true;
}();
console.log('判定结果:' + (result ? '通过' : '不通过'));
```

**31、不借助临时变量，进行两个整数的交换**

``` js
/**
 * 不借助临时变量，进行两个整数的交换
 * 比如：a = 2, b = 4 => a = 4, b =2
 */
function swap() {
    var a = arguments[0];
    var b = arguments[1];

    a = b - a;
    b = b - a;
    a = b + a;

    return [a.b].toString();
}
console.log(swap(10, 12));
```

**32、根据传入的3个参数(边长)number，返回一个数值number代表三角形的类型。**

``` js
// 根据传入的3个参数(边长)number，返回一个数值number代表三角形的类型。
// 提示：可以先算出这个三角形的3个角，然后做比较。
/* 返回 ᐃ 的类型:
  0 : 如果不能构成一个ᐃ
  1 : 锐角ᐃ
  2 : 正角 ᐃ
  3 : 钝角 ᐃ
*/
function triangleType(a, b, c) {
    var max = Math.max(a, b, c);
    if (max >= (a + b + c - max)) {
        return 0;
    }

    var result = max * max - (a * a + b * b + c * c - max * max);
    if (result > 0) {
        return 3;
    } else if (result < 0) {
        return 1;
    } else {
        return 2;
    }
}
triangleType(2, 4, 6); // return 0 (Not triangle)
triangleType(8, 5, 7); // return 1 (Acute, angles are approx. 82°, 38° and 60°)
triangleType(3, 4, 5); // return 2 (Right, angles are approx. 37°, 53° and exactly 90°)
triangleType(7, 12, 8); // return 3 (Obtuse, angles are approx. 34°, 106° and 40°)
```

**33、获取url的search部分，处理为对象并返回**

``` js
/**
 * 获取url的search部分，处理为对象并返回
 * @method getUrlParam
 * @param {String} url
 * @retrun {Object}
 */
function getUrlParam(url) {
    var result = {};
    var search = '';

    if (url) {
        search = url.split('?')[1];
    } else {
        search = location.search.substring(1);
    }

    if (search === "") {
        return "";
    }

    var query = search.split("&");
    for (let i = 0; i < query.length; i++) {
        var match = query[i].match(/([^=]+)=([^=]+)/);
        if (match !== null) {
            result[match[1]] = decodeURIComponent(match[2]);
        }
    }

    return result;
}
```

``` js
/**
 * 获取url的search部分，处理为对象并返回
 * @param {String} url 
 */
function serilizeUrl(url) {
    var result = {};
    url = url.split("?")[1];
    var map = url.split("&");

    for (var i = 0, len = map.length; i < len; i++) {
        var test = map[i];
        if (test) {
            var temp = test.split('=');
            result[temp[0]] = temp[1];
        }
    }
    return result;
}
console.log(serilizeUrl('http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e'))
```

**34、写一个函数，去掉传参的前后空格**

``` js
/**
 * 写一个函数，去掉传参的前后空格
 * @param {String} str 
 */
function trim(str) {
    return str.replace(/^\s+|\s+$/ig, "");
}
```

**35、每个首字母位移到单词末位，然后在每个单词末尾添上ay**

``` js
/**
 * 每个首字母位移到单词末位，然后在每个单词末尾添上ay
 * @param {String} str 
 */
function updateRule(str) {
    return str.split(" ").map(function(v) {
        return v.trim().substr(1) + v.trim()[0] + "ay";
    }).join(" ");
}
console.log(updateRule('Pig latin is cool')); //igPay atinlay siay oolcay
```

**36、完成一个函数，函数接收一个参数function，执行完了之后第二次就失效~**

``` js
/**
 * 完成一个函数，函数接收一个参数function，执行完了之后第二次就失效~
 * @param {Function} fn 
 */
function once(fn) {
    if (typeof fn !== 'function') {
        throw new Error('传入的参数必须是一个函数！');
    }
    return function() {
        return this.n ? "no effect" : (this.n = 1, fn.apply(null, arguments));
    }.bind({
        n: 0
    });
}
```

**37、把多重数组转为一重数组**

``` js
/**
 * 把多重数组转为一重数组
 * @param {Array} arr 
 */
function flatten(arr) {
    return arr.reduce(function(acc, val) {
        return acc.concat(Array.isArray(val) ? flatten(val) : val);
    }, []);
}
console.log(flatten([0, [1, [2, [3, [4, [5, [6]]]]]]]))
```
