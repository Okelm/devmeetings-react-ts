# What's next

### Styling your components:

Well, you can use CSS and CSS processors and then use them as you would if it was simple HTML:

```text
#ready {
  background-color: #123456;
  display: flex;
  justify-content: center;
}
  
  #ready .container {
    padding: 0 10px; 
   }
```

```text
const React = () => (
  <div id='ready'>
    <div className='container'/>
  </div>    
)
```

### CSS-in-JS

But there are more options and the most recent trend is CSS-in-JS. Styled-components is one of the options:

```text
import styled from 'styled-components';

const Ready = styled.div` // or styled(View) in the case of React Native
  background-color: '#123456';
  display: flex,
  justify-content: center,
`;

const Container = styled.div` // or styled(View) in the case of React Native
  padding: 0 10px,
`;

const ReactOrReactNative = () => (
  <Ready>
    <Container/>
  </Ready>    
)
```



