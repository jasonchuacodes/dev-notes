#### Purpose
Used to 'intercept' the data and do actions to it. 
One use-case is to transform the response data - to exclude some set fields.

#### Usage
In this example, we are looping over a set of fields and excluding them in the returned response data.
```ts
import { Injectable, NestInterceptor, ExecutionContext, CallHandler } from '@nestjs/common';
import { Observable } from 'rxjs';
import { map } from 'rxjs/operators';

@Injectable()
export class ExcludeFieldsInterceptor implements NestInterceptor {
  constructor(private readonly excludedFields: string[]) {}

  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {
    return next.handle().pipe(
      map(data => {
        // If the data is an array, we map through each item and exclude the specified fields.
        if (Array.isArray(data)) {
          return data.map(item => this.excludeFields(item));
        }

        // If the data is an object, we directly exclude the specified fields.
        return this.excludeFields(data);
      }),
    );
  }

  private excludeFields(data: any): any {
    for (const field of this.excludedFields) {
      delete data[field];
    }
    return data
  }
}
```

#### Notes
In NestJS, the `pipe()` method is used in conjunction with the `next.handle()` method to handle and modify data as it flows through the middleware chain.

The `pipe()` method is part of the `CallHandler` returned by the interceptors and is similar to the RxJS `pipe()` method. With this we are are then able to transform the incoming data using `map()` or `filter()`.