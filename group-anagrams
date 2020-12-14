给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。
示例:
输入: ["eat", "tea", "tan", "ate", "nat", "bat"]
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]

第一天做leecode上的题目，也是第一天开始github，做的有点不尽人意，但是也要加油噢
1. 首先是自己写的代码，看了下提示添加一个计数的list，然后开始自己写
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        list3 = []
        list5 = []
        for i in strs:
          list2 = [0] * 26
#         创建一个26个字母的计数列表list2  
          for c in i:
            list2[ord(c)-ord("a")] += 1 
#         扫描单词，根据对应的ASCII码，算出对应的小写字母，然后在数列中对应的字母+1
          list3.append(list2)
#         list3为每个单词所对应的26个字母的出现次数
        for i in range(0,len(list3)):
          list4 = []
#         lsit4用于存放每个分类的列表
          if(list3[i] != []):
#           list[i]对应为空的话直接跳过(见23行)
            list4.append(strs[i])
          for j in range(i+1, len(list3)):
            if (list3[j] != []):   
              if (list3[i] == list3[j]):
#               如果list3中对应的每个字母的出现频率相同，则表示的是字母异位词     
                list3[j] = []
#               将j所指向的单词，改为空，i遍历时直接跳过
                list4.append(strs[j])
#               将strs中索引为j的添加到list4中，表示为同一类字母异位词
          if(list4 != []):
            list5.append(list4)
        return list5
2. 后面两种是别人的方法
1). 一个简单的解法就是遍历数组，然后对每一项都进行排序，然后将其添加到 hashTable 中，最后输出 hashTable 中保存的值即可。
这种做法空间复杂度 O(n)， 假设排序算法用的快排，那么时间复杂度为 O(n * klogk), n 为数组长度，k 为字符串的平均长度
var groupAnagrams = function (strs) {
  const hashTable = {};

  function sort(str) {
    return str.split("").sort().join("");
  }

  // 这个方法需要排序，因此不是很优，但是很直观，容易想到
  for (let i = 0; i < strs.length; i++) {
    const str = strs[i];
    const key = sort(str);
    if (!hashTable[key]) {
      hashTable[key] = [str];
    } else {
      hashTable[key].push(str);
    }
  }

  return Object.values(hashTable);
};
2).另外一种跟我写的那种有点类似，不过用的更加快捷的方法进行定位
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        """
        思路同上，在Python中，这里涉及到3个知识点：
        1. 使用内置的 defaultdict 字典设置默认值；
        2. 内置的 ord 函数，计算ASCII值（等于chr）或Unicode值(等于unichr)；
        3. 列表不可哈希，不能作为字典的键，因此这里转为元组；
        """
        str_dict = collections.defaultdict(list)
        for s in strs:
          s_key = [0] * 26
          for c in s:
            s_key[ord(c)-ord('a')] += 1
          str_dict[tuple(s_key)].append(s)
        return list(str_dict.values())

