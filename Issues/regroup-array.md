# Regroup Array

tags: #Issues

記錄自己或朋友遇到的一些業務 issues 解法。

## 1. 原始陣列過濾後重組

問題描述：需要將原始陣列中的值進行過濾，重組後提到第一層，再重組第二層的子陣列，這邊先提供一種解法，後續若有新的解法再補充。

``` JS
// original array

let studentList = [
  {
    id: 1,
    name: '小明',
    class: { name: 'A班' },
  },
  {
    id: 2,
    name: '小王',
    class: { name: 'C班' },
  },
  {
    id: 3,
    name: '小智',
    class: { name: 'C班' },
  },
  {
    id: 4,
    name: '小美',
    class: { name: 'A班' },
  },
  {
    id: 5,
    name: '小智障',
    class: { name: 'B班' },
  },
]
```

``` JS
// expected result

classRoster = [
  {
    name: 'A班',
    students: [
      { id: 1, name: '小明' },
      { id: 4, name: '小美' },
    ]
  },
  {
    name: 'B班',
    students: [
      { id: 5, name: '小智障' },
    ]
  },
  {
    name: 'C班',
    students: [
      { id: 2, name: '小王' },
      { id: 3, name: '小智' },
    ]
  },
]
```

### Solution 1

``` JS
// 整理重複班別名稱
let target = [];
studentList.forEach(node => target.push(node.class.name));
let classNameList = Array.from(new Set(target)).sort();

// 重組陣列
let subTarget = classNameList.map((node) => {
  let item = studentList.filter((subNode) => {
    return subNode.class.name === node;
  });

  let subItem = item.map((val) => {
    return {
      id: val.id,
      name: val.name,
    }
  });

  return {
    name: node,
    students: subItem,
  };
});

console.log(subTarget);
```
