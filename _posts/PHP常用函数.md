# PHP常用函数



## 字符串



- [addcslashes](http://www.pfinal.cn/doc/php/function.addcslashes.html) — 以 C 语言风格使用反斜线转义字符串中的字符
- [addslashes](http://www.pfinal.cn/doc/php/function.addslashes.html) — 使用反斜线引用字符串
- [bin2hex](http://www.pfinal.cn/doc/php/function.bin2hex.html) — 函数把ASCII字符的字符串转换为十六进制值
- [chr](http://www.pfinal.cn/doc/php/function.chr.html) — 返回指定的字符
- [chunk_split](http://www.pfinal.cn/doc/php/function.chunk-split.html) — 将字符串分割成小块
- [crc32](http://www.pfinal.cn/doc/php/function.crc32.html) — 计算一个字符串的 crc32 多项式
- [crypt](http://www.pfinal.cn/doc/php/function.crypt.html) — 单向字符串散列
- [echo](http://www.pfinal.cn/doc/php/function.echo.html) — 输出一个或多个字符串
- [explode](http://www.pfinal.cn/doc/php/function.explode.html) — 使用一个字符串分割另一个字符串
- [fprintf](http://www.pfinal.cn/doc/php/function.fprintf.html) — 将格式化后的字符串写入到流
- [hex2bin](http://www.pfinal.cn/doc/php/function.hex2bin.html) — 转换十六进制字符串为二进制字符串
- [html_entity_decode](http://www.pfinal.cn/doc/php/function.html-entity-decode.html) — Convert all HTML entities to their applicable characters
- [htmlentities](http://www.pfinal.cn/doc/php/function.htmlentities.html) — Convert all applicable characters to HTML entities
- [htmlspecialchars_decode](http://www.pfinal.cn/doc/php/function.htmlspecialchars-decode.html) — 将特殊的 HTML 实体转换回普通字符
- [htmlspecialchars](http://www.pfinal.cn/doc/php/function.htmlspecialchars.html) — Convert special characters to HTML entities
- [implode](http://www.pfinal.cn/doc/php/function.implode.html) — 将一个一维数组的值转化为字符串
- [join](http://www.pfinal.cn/doc/php/function.join.html) — 别名 implode
- [lcfirst](http://www.pfinal.cn/doc/php/function.lcfirst.html) — 使一个字符串的第一个字符小写
- [ltrim](http://www.pfinal.cn/doc/php/function.ltrim.html) — 删除字符串开头的空白字符（或其他字符）
- [md5_file](http://www.pfinal.cn/doc/php/function.md5-file.html) — 计算指定文件的 MD5 散列值
- [md5](http://www.pfinal.cn/doc/php/function.md5.html) — 计算字符串的 MD5 散列值
- [money_format](http://www.pfinal.cn/doc/php/function.money-format.html) — Formats a number as a currency string
- [nl2br](http://www.pfinal.cn/doc/php/function.nl2br.html) — 在字符串所有新行之前插入 HTML 换行标记
- [number_format](http://www.pfinal.cn/doc/php/function.number-format.html) — 以千位分隔符方式格式化一个数字
- [ord](http://www.pfinal.cn/doc/php/function.ord.html) — 返回字符的 ASCII 码值
- [parse_str](http://www.pfinal.cn/doc/php/function.parse-str.html) — 将字符串解析成多个变量
- [print](http://www.pfinal.cn/doc/php/function.print.html) — 输出字符串
- [printf](http://www.pfinal.cn/doc/php/function.printf.html) — 输出格式化字符串
- [rtrim](http://www.pfinal.cn/doc/php/function.rtrim.html) — 删除字符串末端的空白字符（或者其他字符）
- [sha1](http://www.pfinal.cn/doc/php/function.sha1.html) — 计算字符串的 sha1 散列值
- [sprintf](http://www.pfinal.cn/doc/php/function.sprintf.html) — Return a formatted string
- [sscanf](http://www.pfinal.cn/doc/php/function.sscanf.html) — 根据指定格式解析输入的字符
- [str_getcsv](http://www.pfinal.cn/doc/php/function.str-getcsv.html) — 解析 CSV 字符串为一个数组
- [str_ireplace](http://www.pfinal.cn/doc/php/function.str-ireplace.html) — str_replace 的忽略大小写版本
- [str_pad](http://www.pfinal.cn/doc/php/function.str-pad.html) — 使用另一个字符串填充字符串为指定长度
- [str_repeat](http://www.pfinal.cn/doc/php/function.str-repeat.html) — 重复一个字符串
- [str_replace](http://www.pfinal.cn/doc/php/function.str-replace.html) — 子字符串替换
- [str_shuffle](http://www.pfinal.cn/doc/php/function.str-shuffle.html) — 随机打乱一个字符串
- [str_split](http://www.pfinal.cn/doc/php/function.str-split.html) — 将字符串转换为数组
- [str_word_count](http://www.pfinal.cn/doc/php/function.str-word-count.html) — 返回字符串中单词的使用情况
- [strcasecmp](http://www.pfinal.cn/doc/php/function.strcasecmp.html) — 二进制安全比较字符串（不区分大小写）
- [strchr](http://www.pfinal.cn/doc/php/function.strchr.html) — 别名 strstr
- [strcmp](http://www.pfinal.cn/doc/php/function.strcmp.html) — 二进制安全字符串比较
- [strip_tags](http://www.pfinal.cn/doc/php/function.strip-tags.html) — 从字符串中去除 HTML 和 PHP 标记
- [stripcslashes](http://www.pfinal.cn/doc/php/function.stripcslashes.html) — 反引用一个使用 addcslashes 转义的字符串
- [stripos](http://www.pfinal.cn/doc/php/function.stripos.html) — 查找字符串首次出现的位置（不区分大小写）
- [stripslashes](http://www.pfinal.cn/doc/php/function.stripslashes.html) — 反引用一个引用字符串
- [stristr](http://www.pfinal.cn/doc/php/function.stristr.html) — strstr 函数的忽略大小写版本
- [strlen](http://www.pfinal.cn/doc/php/function.strlen.html) — 获取字符串长度
- [strnatcasecmp](http://www.pfinal.cn/doc/php/function.strnatcasecmp.html) — 使用“自然顺序”算法比较字符串（不区分大小写）
- [strnatcmp](http://www.pfinal.cn/doc/php/function.strnatcmp.html) — 使用自然排序算法比较字符串
- [strncasecmp](http://www.pfinal.cn/doc/php/function.strncasecmp.html) — 二进制安全比较字符串开头的若干个字符（不区分大小写）
- [strncmp](http://www.pfinal.cn/doc/php/function.strncmp.html) — 二进制安全比较字符串开头的若干个字符
- [strpbrk](http://www.pfinal.cn/doc/php/function.strpbrk.html) — 在字符串中查找一组字符的任何一个字符
- [strpos](http://www.pfinal.cn/doc/php/function.strpos.html) — 查找字符串首次出现的位置
- [strrchr](http://www.pfinal.cn/doc/php/function.strrchr.html) — 查找指定字符在字符串中的最后一次出现
- [strrev](http://www.pfinal.cn/doc/php/function.strrev.html) — 反转字符串
- [strripos](http://www.pfinal.cn/doc/php/function.strripos.html) — 计算指定字符串在目标字符串中最后一次出现的位置（不区分大小写）
- [strrpos](http://www.pfinal.cn/doc/php/function.strrpos.html) — 计算指定字符串在目标字符串中最后一次出现的位置
- [strstr](http://www.pfinal.cn/doc/php/function.strstr.html) — 查找字符串的首次出现
- [strtok](http://www.pfinal.cn/doc/php/function.strtok.html) — 标记分割字符串
- [strtolower](http://www.pfinal.cn/doc/php/function.strtolower.html) — 将字符串转化为小写
- [strtoupper](http://www.pfinal.cn/doc/php/function.strtoupper.html) — 将字符串转化为大写
- [strtr](http://www.pfinal.cn/doc/php/function.strtr.html) — 转换指定字符
- [substr_compare](http://www.pfinal.cn/doc/php/function.substr-compare.html) — 二进制安全比较字符串（从偏移位置比较指定长度）
- [substr_count](http://www.pfinal.cn/doc/php/function.substr-count.html) — 计算字串出现的次数
- [substr_replace](http://www.pfinal.cn/doc/php/function.substr-replace.html) — 替换字符串的子串
- [substr](http://www.pfinal.cn/doc/php/function.substr.html) — 返回字符串的子串
- [trim](http://www.pfinal.cn/doc/php/function.trim.html) — 去除字符串首尾处的空白字符（或者其他字符）
- [ucfirst](http://www.pfinal.cn/doc/php/function.ucfirst.html) — 将字符串的首字母转换为大写
- [ucwords](http://www.pfinal.cn/doc/php/function.ucwords.html) — 将字符串中每个单词的首字母转换为大写
- [vfprintf](http://www.pfinal.cn/doc/php/function.vfprintf.html) — 将格式化字符串写入流
- [vprintf](http://www.pfinal.cn/doc/php/function.vprintf.html) — 输出格式化字符串
- [vsprintf](http://www.pfinal.cn/doc/php/function.vsprintf.html) — 返回格式化字符串
- [wordwrap](http://www.pfinal.cn/doc/php/function.wordwrap.html) — 打断字符串为指定数量的字串



## 数组



- [array_chunk](http://www.pfinal.cn/doc/php/function.array-chunk.html) — 将一个数组分割成多个
- [array_column](http://www.pfinal.cn/doc/php/function.array-column.html) — 返回数组中指定的一列
- [array_combine](http://www.pfinal.cn/doc/php/function.array-combine.html) — 创建一个数组，用一个数组的值作为其键名，另一个数组的值作为其值
- [array_count_values](http://www.pfinal.cn/doc/php/function.array-count-values.html) — 统计数组中所有的值出现的次数
- [array_diff](http://www.pfinal.cn/doc/php/function.array-diff.html) — 计算数组的差集
- [array_fill_keys](http://www.pfinal.cn/doc/php/function.array-fill-keys.html) — 使用指定的键和值填充数组
- [array_fill](http://www.pfinal.cn/doc/php/function.array-fill.html) — 用给定的值填充数组
- [array_filter](http://www.pfinal.cn/doc/php/function.array-filter.html) — 用回调函数过滤数组中的单元
- [array_flip](http://www.pfinal.cn/doc/php/function.array-flip.html) — 交换数组中的键和值
- [array_intersect](http://www.pfinal.cn/doc/php/function.array-intersect.html) — 计算数组的交集
- [array_key_exists](http://www.pfinal.cn/doc/php/function.array-key-exists.html) — 检查给定的键名或索引是否存在于数组中
- [array_keys](http://www.pfinal.cn/doc/php/function.array-keys.html) — 返回数组中部分的或所有的键名
- [array_map](http://www.pfinal.cn/doc/php/function.array-map.html) — 将回调函数作用到给定数组的单元上
- [array_merge_recursive](http://www.pfinal.cn/doc/php/function.array-merge-recursive.html) — 递归地合并一个或多个数组
- [array_merge](http://www.pfinal.cn/doc/php/function.array-merge.html) — 合并一个或多个数组
- [array_multisort](http://www.pfinal.cn/doc/php/function.array-multisort.html) — 对多个数组或多维数组进行排序
- [array_pad](http://www.pfinal.cn/doc/php/function.array-pad.html) — 用值将数组填补到指定长度
- [array_pop](http://www.pfinal.cn/doc/php/function.array-pop.html) — 将数组最后一个单元弹出（出栈）
- [array_push](http://www.pfinal.cn/doc/php/function.array-push.html) — 将一个或多个单元压入数组的末尾（入栈）
- [array_rand](http://www.pfinal.cn/doc/php/function.array-rand.html) — 从数组中随机取出一个或多个单元
- [array_replace](http://www.pfinal.cn/doc/php/function.array-replace.html) — 使用传递的数组替换第一个数组的元素
- [array_reverse](http://www.pfinal.cn/doc/php/function.array-reverse.html) — 返回一个单元顺序相反的数组
- [array_search](http://www.pfinal.cn/doc/php/function.array-search.html) — 在数组中搜索给定的值，如果成功则返回相应的键名
- [array_shift](http://www.pfinal.cn/doc/php/function.array-shift.html) — 将数组开头的单元移出数组
- [array_slice](http://www.pfinal.cn/doc/php/function.array-slice.html) — 从数组中取出一段
- [array_splice](http://www.pfinal.cn/doc/php/function.array-splice.html) — 把数组中的一部分去掉并用其它值取代
- [array_sum](http://www.pfinal.cn/doc/php/function.array-sum.html) — 计算数组中所有值的和
- [array_udiff](http://www.pfinal.cn/doc/php/function.array-udiff.html) — 用回调函数比较数据来计算数组的差集
- [array_unique](http://www.pfinal.cn/doc/php/function.array-unique.html) — 移除数组中重复的值
- [array_unshift](http://www.pfinal.cn/doc/php/function.array-unshift.html) — 在数组开头插入一个或多个单元
- [array_values](http://www.pfinal.cn/doc/php/function.array-values.html) — 返回数组中所有的值
- [array_walk](http://www.pfinal.cn/doc/php/function.array-walk.html) — 使用用户自定义函数对数组中的每个元素做回调处理
- [array](http://www.pfinal.cn/doc/php/function.array.html) — 新建一个数组
- [arsort](http://www.pfinal.cn/doc/php/function.arsort.html) — 对数组进行逆向排序并保持索引关系
- [asort](http://www.pfinal.cn/doc/php/function.asort.html) — 对数组进行排序并保持索引关系
- [compact](http://www.pfinal.cn/doc/php/function.compact.html) — 建立一个数组，包括变量名和它们的值
- [count](http://www.pfinal.cn/doc/php/function.count.html) — 计算数组中的单元数目或对象中的属性个数
- [current](http://www.pfinal.cn/doc/php/function.current.html) — 返回数组中的当前单元
- [each](http://www.pfinal.cn/doc/php/function.each.html) — 返回数组中当前的键／值对并将数组指针向前移动一步
- [end](http://www.pfinal.cn/doc/php/function.end.html) — 将数组的内部指针指向最后一个单元
- [extract](http://www.pfinal.cn/doc/php/function.extract.html) — 从数组中将变量导入到当前的符号表
- [in_array](http://www.pfinal.cn/doc/php/function.in-array.html) — 检查数组中是否存在某个值
- [key_exists](http://www.pfinal.cn/doc/php/function.key-exists.html) — 别名 array_key_exists
- [key](http://www.pfinal.cn/doc/php/function.key.html) — 从关联数组中取得键名
- [krsort](http://www.pfinal.cn/doc/php/function.krsort.html) — 对数组按照键名逆向排序
- [ksort](http://www.pfinal.cn/doc/php/function.ksort.html) — 对数组按照键名排序
- [list](http://www.pfinal.cn/doc/php/function.list.html) — 把数组中的值赋给一些变量
- [natsort](http://www.pfinal.cn/doc/php/function.natsort.html) — 用“自然排序”算法对数组排序
- [next](http://www.pfinal.cn/doc/php/function.next.html) — 将数组中的内部指针向前移动一位
- [pos](http://www.pfinal.cn/doc/php/function.pos.html) — current 的别名
- [prev](http://www.pfinal.cn/doc/php/function.prev.html) — 将数组的内部指针倒回一位
- [range](http://www.pfinal.cn/doc/php/function.range.html) — 建立一个包含指定范围单元的数组
- [reset](http://www.pfinal.cn/doc/php/function.reset.html) — 将数组的内部指针指向第一个单元
- [rsort](http://www.pfinal.cn/doc/php/function.rsort.html) — 对数组逆向排序
- [shuffle](http://www.pfinal.cn/doc/php/function.shuffle.html) — 将数组打乱
- [sizeof](http://www.pfinal.cn/doc/php/function.sizeof.html) — count 的别名
- [sort](http://www.pfinal.cn/doc/php/function.sort.html) — 对数组排序
- [uasort](http://www.pfinal.cn/doc/php/function.uasort.html) — 使用用户自定义的比较函数对数组中的值进行排序并保持索引关联
- [uksort](http://www.pfinal.cn/doc/php/function.uksort.html) — 使用用户自定义的比较函数对数组中的键名进行排序
- [usort](http://www.pfinal.cn/doc/php/function.usort.html) — 使用用户自定义的比较函数对数组中的值进行排序