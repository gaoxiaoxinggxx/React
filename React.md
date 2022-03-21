## 1：React

### 1.1：文件目录介绍

```
1：父组件给子组件传值
2：父组件调用子组件方法
3：子组件给父组件传值
4：子组件调用父组件方法
```

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
class Example extends React.Component{
    state = {count:0,num:9999}
    
    addCount = ()=>{
        this.setState({count:this.state.count + 1})
    }
    addNum =() => this.setState({num:this.state.num})
    render(){
        return (
        <div>
            <p>You clicked {this.state.count} times</p>
             <button onClick={this.addCount}>
               Click me add count
             </button>
             <button onClick={this.addNum}>
               Click me add num
             </button>
        </div>
    )}
}
export default Example

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
export type TimerProps = {
    seconds: number
}

class Timer extends React.Component<TimerProps>{
    timerId : any = undefined
    state = {num:this.props.seconds}
    componentDidMount(){
       this.timerId = setInterval(()=>{
           if(this.state.num>0){
             this.setState({num:this.state.num-1})
           }else{
            clearInterval(this.timerId)
            console.log('执行完了')
           }
       },1000)
      }
      componentWillUnmount(){
          clearInterval(this.timerId)
      }
    render(){
        //const seconds = this.props
        return (
            <div>当前秒是{this.state.num}</div>
        )
    }
}
export default Timer
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

### 
