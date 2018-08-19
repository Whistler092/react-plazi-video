## Profundizar React
“React in Patterns” Krasimir Tsonev.
https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Spread_operator
https://reactjs.org/docs/handling-events.html

## ¿Que es un Component?

Los Component (Componente) son como las funciones de JavaScript. Aceptan entradas arbitrarias (llamadas “props”) y retornan los elementos que describen lo que debería aparecer en la pantalla.
Documentacion Oficial.

## ¿Tipos de Components?

```
Funcional: Este tipo de componentes se definen como funciones y no tiene ni trabajan con estados.

Puro: También se implementan como clases, pero en este caso van a extender de React.PureComponent.

Normal o de Estado: Las principales características de este tipo de componentes es que utilizan la encapsulación en clases, tienen un estado que definen, y actualizan.

Nota: Los componentes Funcionales se utilizan para codear la UI mientras que el Normal o el Puro se utiliza para codear la “logica”.
```

## PropTypes
$ npm install prop-types --save
```

Hay que validar los datos (Objetos, Arreglos, Numeros, Strings o Funciones) en nuestras aplicaciones, ya que podríamos recibir datos inesperados que pueden afectar (o incluso a romper) nuestra aplicación.

Para eso React nos provee de PropTypes.

$ npm install prop-types -S
Diferencia de propTypes y PropTypes:

PropTypes es el componente que importamos e instalamos por npm, el cual nos ayuda a validar los tipos de dato:

import PropTypes from'prop-types';
Y propTypes es un atributo de la clase Component de react:

Media.propTypes = {
  image: PropTypes.string,
  title: PropTypes.string,
  author: PropTypes.string,
  type: PropTypes.oneOf(['video', 'audio'])
}
```

## Enlazando eventos del DOM
```
https://reactjs.org/docs/handling-events.html

Para enlazar los eventos que reaccionen a un click dentro de los componentes, hay que utilizar onClick (on + el evento) y a esta le asignamos una función a ejecutar handleClick dentro del elemento que va a lanzar el evento.

<divclassName="Media"onClick={this.handleClick}>

Para enlazar las propiedades (props) de nuestro componente a la clase Media, hay que utilizar el metodo constructor pasandole props y usando el metodo super tambien con las props como parametro.

Es necesario cambiar el contexto de la función handleClick, para eso utilizamos bind(this).

constructor(props){
    super(props);
    this.handleClick = this.handleClick.bind(this);
}
Con ES7, en lugar de estar bindeando cada función de nuestro componente, podemos utilizar arrow functions.

handleClick = (event) => {
    console.log(this.props.title);
}
A handleClick le asignamos una arrow function que recibe el evento y realiza las acciones.
Esto funciona debido a que las arrow functions hederan el contexto del padre, así no es necesario bindear.

```

## El estado 
```
Las propiedades (props) son inmutables, es decir; estas no pueden cambiar. En el caso que quisiéramos que algo cambie en nuestro componente, hay que manejarlo con el estado de nuestros componentes, el cual permite tener contenido dinámico.

Para inicializar el estado tenemos que hacer uso de nuestro metodo constructor:

constructor(props){
    super(props);
    this.state = {
        author: props.author
    }
}
Y en nuestros elementos vamos a utilizar state en lugar de props:

<p className="Media-author">{this.state.author}</p>
Para cambiar el estado tenemos un método especifico setSate() al cual le pasamos los valores que queremos modificar en nuestro estado.

handleClick = (event) => {
    this.setState({
        author: 'Emmanuel Alonso'
    })
}
Con ES7 podemos hacer definir el estado directamente, en lugar de usar el constructor:

state = {
    author: 'Ivan Robles'
}
```

## Ciclo de vida de un componente 

```
class MiComponente extends Components{

	constructor(){
	// Enlazo (bind) eventos y/o inicializo estado
	}
	componentWillMount(){
	// Se ejecuta antes de montar el componente
	// Se podría usar para hacer un setState()
	}
	render(){
	// Contiene todos los elementos a renderizar
	// podrías usarlo para calcular propiedades (ej: concatenar una cadena)
	}
	componentDidMount(){
	//Solo se lanza una vez
	//Ideal para llamar a una API, hacer un setInteval, etc
	}

	//Actualización:
	componentWillReceiveProps(){
	//Es llamado cuando el componente recibe nuevas propiedades.

	}
	shouldComponentUpdate(){
	//Idea para poner una condición y  si las propiedades que le llegaron anteriormente
	// eran las mismas que tenia retornar false para evitar re-renderear el componente
	}
	componentWillUpdate(){
	//metodo llamado antes de re-renderizar el componente si shouldComponentUpdate devolvió true
	}

	// re-render si es necesario...

	componentDidUpdate(){
	//Método llamado luego del re-render
	}
	componentWillUnmount(){
	//Método llamado antes de desmontar el componente
	}
	componentDidCatch(){
	// Si ocurre algún error, lo capturo desde acá:
	}

}
```

##Spread Operator
https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Spread_operator
