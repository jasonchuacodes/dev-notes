`php artisan make:request MyRequestName`

With Laravel Form Request, we can set custom validation rules, validation messages, setup attributes before validation, etc.

Take this example of a Form Request for input file.
```php
class IfManufacturingPlanRequest extends FormRequest
{
    protected $stopOnFirstFailure = true;

    public function authorize()
    {
        return true;
    }

// actions before validation (optional)
    protected function prepareForValidation()
    {
        $this->merge([
            'file_name' => $this->file->getClientOriginalName(),
        ]);
    }

// validation rules
	public function rules()
    {
        return [
            'file' => 'required|mimes:xlsx,xls|max:10240',
            'file_name' => 'required',
        ];
    }

// failed validation messages
    public function messages()
    {
        return [
            'file' => __('multi-lang.error-went-wrong'),
            'file_name' => __('multi-lang.error-went-wrong'),
        ];
    }
}
```

We can also use the [[$this]] keyword to access the arguments passed by the request such as the `file` passed in the `input field`. 