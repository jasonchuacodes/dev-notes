Example:
```js
type CreateDialogState = {
  openDialog: boolean
  documentType?: 'Document' | 'Contract' | 'DeliverySlip'
}

const [dialogState, setDialogState] =
    useState<CreateDocumentDialogState>({
      openDialog: false,
      documentType: undefined,
    })
```
Note here that within our useState, we have defined an object with two (2) properties.
```js
{
  openDialog: false,
  documentType: undefined,
}
```