<!--
### Hi there 👋

**ddhienpy/ddhienpy** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

# Build tree from flat array

```js
function buildTree(nodes, parentId = null) {
  const tree = [];
  for (const node of nodes) {
    if (node.parentId === parentId) {
      const children = buildTree(nodes, node.id);
      if (children.length) {
        node.children = children;
      }
      tree.push(node);
    }
  }
  return tree;
}
```

```js
const flatArray = [
  { id: 1, name: "Node 1", parentId: null },
  { id: 2, name: "Node 1.1", parentId: 1 },
  { id: 3, name: "Node 1.1.1", parentId: 2 },
  { id: 4, name: "Node 4", parentId: null },
  { id: 5, name: "Node 4.1", parentId: 4 },
  { id: 6, name: "Node 4.1.1", parentId: 5 },
];

const tree = buildTree(flatList);
console.log(JSON.stringify(tree, null, 2));
```

```js
[
  {
    "id": 1,
    "name": "Node 1",
    "parentId": null,
    "children": [
      {
        "id": 2,
        "name": "Node 1.1",
        "parentId": 1,
        "children": [
          {
            "id": 3,
            "name": "Node 1.1.1",
            "parentId": 2
          }
        ]
      }
    ]
  },
  {
    "id": 4,
    "name": "Node 4",
    "parentId": null,
    "children": [
      {
        "id": 5,
        "name": "Node 4.1",
        "parentId": 4,
        "children": [
          {
            "id": 6,
            "name": "Node 4.1.1",
            "parentId": 5
          }
        ]
      }
    ]
  }
]
```


# Spread properties in an object

```
const obj = {
  ...(someCondition ? {a : 1} : {b: 2}),
  ...(otherCondition && {c : 3})
}
```

# Flatten array in JS

```
[1, 2, 3, [4, 5, [6, 7]]].flat() // >> [1, 2, 3, 4, 5, [6, 7]]

// deep flat
[1, 2, 3, [4, 5, [6, 7]]].flat(Infinity) // >> [1, 2, 3, 4, 5, 6, 7]
```

# Deploy nodejs app with gitlab.com and pm2

```
https://gist.github.com/zmts/98aec1c033e460a51da74acd74b22609
```

# Get image width and height with JavaScript

```js
function imageSize (image) {
  return new Promise((resolve, reject) => {
    try {
      const fileReader = new FileReader()

      fileReader.onload = () => {
        const img = new Image()

        img.onload = () => {
          resolve({ width: img.width, height: img.height })
        }

        img.src = fileReader.result
      }

      fileReader.readAsDataURL(image)
    } catch (e) {
      reject(e)
    }
  })
}
```

