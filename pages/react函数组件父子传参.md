- #react
	- ```js
	  
	  // 子组件
	  import React, { forwardRef, useImperativeHandle, useRef } from 'react';
	  
	  type ChildProps = {
	    // 子组件的其他 props
	  };
	  
	  type ChildMethods = {
	    // 子组件暴露给父组件的方法
	    someMethod: () => void;
	  };
	  
	  const ChildComponent: React.ForwardRefRenderFunction<ChildMethods, ChildProps> = ({}, ref) => {
	    // 子组件的其他代码...
	  
	    const someMethod = () => {
	      // 子组件的方法实现
	      console.log('Child method called!');
	    };
	  
	    // 将子组件的方法暴露给父组件
	    useImperativeHandle(ref, () => ({
	      someMethod,
	    }));
	  
	    return <div>Child Component</div>;
	  };
	  
	  export default forwardRef(ChildComponent);
	  
	  ```
	- ```js
	  // 父组件
	  import React, { useRef } from 'react';
	  import ChildComponent, { ChildMethods } from './ChildComponent';
	  
	  const ParentComponent: React.FC = () => {
	    const childRef = useRef<ChildMethods>(null);
	  
	    const handleClick = () => {
	      // 通过子组件的引用调用子组件的方法
	      if (childRef.current) {
	        childRef.current.someMethod();
	      }
	    };
	  
	    return (
	      <div>
	        <ChildComponent ref={childRef} />
	        <button onClick={handleClick}>Call Child Method</button>
	      </div>
	    );
	  };
	  
	  export default ParentComponent;
	  ```