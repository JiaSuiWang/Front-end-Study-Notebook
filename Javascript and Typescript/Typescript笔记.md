# Typescript笔记

#### Interface

 An interface is a syntactical contract that an entity should conform to. 

```typescript
interface LabeledValue {
  label: string;
}

function printLabel(labeledObj: LabeledValue) {
  console.log(labeledObj.label);
}
```

这段代码表示：

1.函数printLabel有一个参数是labeledObj，这个参数必须满足

LabeledValue接口，意味着必须有一个string类型的变量



#### Optional Properties

```typescript
interface SquareConfig {
  color?: string;
  width?: number;

}
```



