---
emoji: 📚
title: Redux
date: '2023-01-10 09:18:00'
author: 권형석
tags: Redux frontend
categories: Redux
---

#### 기존에 사용했던 recoil 이외의 전역상태관리 라이브러리인 redux를 학습하며 정리합니다. 

# useSelector()   

useSelector는 Redux store로부터 state를 가져올 때 사용한다.
```
import {createStore} from "redux";

const store = createStore(reducer);

export default store;

```   
# useDispatch()
useDispatch는 action을 reducer로 dispatch할 때 사용할 수 있는 훅이다. (reducer로 dispatch하여 기존의 state를 `대체`한다)
```
import {useDispatch} from "react-redux"

const dispatch = useDispatch();

dispatch(ACTION)
```

<hr/>

### 리덕스 작업을 위해서는 3개의 파일을 생성해야 한다.
><li/>action   

>action을 생성하고, 해당 action이 어떤 일을 수행할지 지정한다.   

><li/>reducer   

>dispatch된 action을 실행시킬 reducer
>action 객체를 받아 기존의 state를 대체시킨다. 

><li/>store   

>reducer로 `global store`를 만든다   


   
<br/>

#### 간단한 todo-list를 만들기 위해 todo를 추가하고 삭제하는 action을 만든다.
```
export const add_todo = (todo) => {
    return {
        type:ADD,
        todo:{
            id: id++,
            title: todo.title,
            isComplete: todo.isComplete,
        }
    }
};

export const delete_todo = (id) => {
    return {
        type: DELETE,
        id,
    }
};
```
todo를 추가하기위해 매개변수로 받은 todo 객체를 reducer에게 반환하고, todo를 삭제하기 위해서는 삭제하려는 todo의 id만을 넘겨준다.
```
const initialState = {
    todos:[],
};

// action을 받아서 새로운 객체를 형성하고, store의 객체를 대체한다
export const reducers = (state = initialState, action) => {
    if (action.type === ADD){
        return{
            todos:[...state.todos, action.todo],
        };
    }
    
    if (action.type === DELETE) {
        return {
            todos:[...state.todos.filter((todo) => todo.id !== action.id)]
        }
    }

}
```
>`[ADD]`initialState로 todos라는 빈 배열을 만들고, 이 배열에 새로운 항목을 추가한 `새로운 state`를 반환하도록 한다.   

>`[DELETE]`action이 넘겨줄 id를 가지고 `Array.filter()` 메서드를 이용해 id가 동일한 todo 객체를 삭제한 todos를 반환하도록 한다.`

### store
```
import {createStore} from "redux";

const store = createStore(reducer);

export default store;
```
리덕스 store에 reducer를 넣어주는 작업을 해당 파일에서 수행한다.


## InputForm
```
export default function InputForm() {

    const dispatch = useDispatch();
    const [text, setText] = useState("");

    const handleChange = (e: any) => {
        const {value} = e.target;
        setText(value);
        // console.log("text", text)
    };

    const handleClick = () => {
        if (text.trim() === ''){
            alert("글자를 입력해주세요");
            return;
        };
        const todo = {
            title: text,
            isComplete:false,
        }
        // action을 dispatch
        dispatch(add_todo(todo));
        alert("입력되었습니다");
        setText("");

    };

    const handleKeyPress = (e:any) => {
        if(e.key === "Enter"){
            handleClick();
        }
    };


  return (
    <Wrapper>
        <Input placeholder='Write down your todos' onChange={handleChange} onKeyDown={handleKeyPress}/>
        <Buttons onClick={handleClick}>Add</Buttons>
    </Wrapper>
  )
}
```
   
## todoItem
```
export default function TodoItem({todo}) {
    const dispatch = useDispatch();

    const {id, title, isComplete} = todo;



    // action(delete_todo)을 dispatch한다.
    const handleClick = () => {
        dispatch(delete_todo(id))
    }
  return (
    <Wrapper>
      <input type="checkbox" onClick={handleCheck}/>
        <Title>{title}</Title>
        {/* <div onClick={handleClick}>x</div> */}
        <IconWrapper>
          <BsPen style={{cursor:'pointer', marginRight:'20px'}}/>
          <BsTrash onClick={handleClick} style={{cursor:'pointer'}}/>
        </IconWrapper>
    </Wrapper>
  )
}
```
여기에서는 todo item을 삭제, 즉 해당 todo를 완료했을 경우를 위해 DELETE ACTION을 dispatch한다. 이를 위해 useDispatch()를 사용했다.

## todoList
```
export default function TodoList() {
    const todos = useSelector((state:any) => state?.todos);

  return (
        <Wrapper>
          {todos?.map((todo:any) => (
              <TodoItem key={todo.id} todo={todo}></TodoItem>
          ))}
         </Wrapper>
    
  )
}
```
