## 1：React

### 1.1：文件目录介绍

### 1.2：Hook API

#### 1.2.1：useState

```react
#FC
export type TimerProps = {
    seconds: number
}
const Timer : React.FC<TimerProps> = (props)=>{
    const [seconds,setSeconds] = useState(props.seconds);

    useEffect(()=>{
       setSeconds(seconds-1)
    },[seconds])

    return <div>当前秒是{seconds}</div>
}

#Class

```

#### 1.2.2：useEffect

```react
#FC
const Example : React.FC = ()=>{
    const [count, setCount] = useState(0);
    const [num,setNum] = useState(9999);
    // 相当于 componentDidMount 和 componentDidUpdate:
    // 组件加载成功执行一次，useEffect(()=>{},[]) 第二个为空数组，则只会在加载成功的时候执行一次
    useEffect(() => {
        // 使用浏览器的 API 更新页面标题
        //document.title = `You clicked ${count} times`;
        console.log('组件加载成功')
      },[]);
    // 组件根据state状态更改的时候执行， useEffect(()=>{},[count]) 
    useEffect(()=>{
        document.title = `You clicked ${count} times`;
    },[count])
    // 组件在卸载的时候 
    useEffect(()=>{
        return ()=>{
            alert('组件卸载了')
        }
    },[])

    return (
        <div>
            <p>You clicked {count} times</p>
             <button onClick={() => setCount(count + 1)}>
               Click me add count
             </button>
             <button onClick={() => setNum(num - 1)}>
               Click me add num
             </button>
        </div>
    )
}
#Class
```

#### 1.2.3：useContext

```react
1：使用React Context API,在组件外部建立一个Context
2：CountContext.Provider提供了一个Context对象，这个对象可以被子组件共享
3：useContext()钩子函数用来引入Context对象，从中获取count属性

```

#### 1.2.4：useReducer

#### 1.2.5：useCallback

#### 1.2.6：useMemo

#### 1.2.7：useRef

#### 1.2.8：useImperativeHandle

#### 1.2.9：useLayoutEffect

#### 1.3.10：useDebugValue
