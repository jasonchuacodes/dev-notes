```ts
export type ValueOf<T> = T[keyof T]

export const CreateDocumentEnum = {
  DOCUMENT: 'Document',
  CONTRACT: 'Contract',
  DELIVERY_SLIP: 'Delivery_Slip',
} as const

export type CreateDocumentType = ValueOf<typeof CreateDocumentEnum>
```
We have extracted the values `'Document' | 'Contract' | 'Delivery_Slip'` and assigned it as a literal type to CreateDocumentType.

Note that we have placed `as const` in the definition of CreateDocumentEnum. This is needed so that TS would treat this as a literal type and not give it a generic type of `string`.