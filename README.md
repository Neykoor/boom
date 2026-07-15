# @neykoor/boom

Error HTTP-friendly, subconjunto reducido de la API de `@hapi/boom`, con solo lo que usa BaileysX. Sin dependencias externas (no requiere `@hapi/hoek`). ESM puro.

## Instalación

```
npm install @neykoor/boom
```

## API

```ts
import { Boom } from '@neykoor/boom'

throw new Boom('mensaje de error')
throw new Boom('mensaje de error', { statusCode: 404 })
throw new Boom('mensaje de error', { statusCode: 400, data: { foo: 'bar' } })

try {
	// ...
} catch (error) {
	if (error instanceof Boom) {
		console.log(error.output.statusCode)
		console.log(error.data)
	}
}
```

## Diferencias con @hapi/boom

- Solo incluye el constructor `Boom(message, options)` con `statusCode` y `data`.
- No incluye los helpers estáticos (`Boom.badRequest`, `Boom.notFound`, etc.), `boomify`, ni `isBoom` como función exportada.
- `instanceof Boom` funciona mediante la cadena de prototipos normal de JavaScript, sin necesidad del truco `Symbol.hasInstance` que usa el original.
