### Summary

This repository enhances the functionality of the Zod (version 4) library by providing validation decorators. Zod is a TypeScript-first schema declaration and validation library. The added decorators make it easier to validate data against predefined schemas in TypeScript projects. This package is based on Jordi Bermejo's ts-zod-decorators package.

### Installation

```
npm install ts-zod4-decorators
```

### Input validation

```ts
import { ZodInput, Validate } from 'ts-zod-decorators';
import * as z from 'zod';

const schema = z.object({ name: z.string(), age: z.number() });

class Foo {
	@Validate
	public bar(@ZodInput(schema) input: z.infer<typeof schema>) {}
}
```

### Output validation

```ts
import { ZodInput, Validate, ZodOutput } from 'ts-zod-decorators';
import * as z from 'zod';

const schema = z.object({ name: z.string(), age: z.number() });

class Foo {
	@Validate
	@ZodOutput(schema)
	public bar(input: unknown): Promise<z.infer<schema>> {
		return Promise.resolve({ name: 'foo', age: 1 });
	}
}
```
