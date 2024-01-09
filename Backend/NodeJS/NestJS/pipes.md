#### Purpose
handles data transformation and validation at a more granular level, typically focused on specific data elements like parameters or request bodies.

There are a lot of pipes available - for validation, parsing, etc. 
Examples include `ValidationPipe`, `ParseIntPipe`, `ParseBoolPipe` 

#### Examples
`ValidationPipe` - used to run the built-in validation in NestJS. Needs defined DTOs to work.

```js
@Post()
@UsePipes(new ValidationPipe({ transform: true }))
async create(@Body() params: CreateJobDto): Promise<Job> {
	const job = await this.jobService.createJob(params)

	return job;
}
```

`ParseIntPipe` - used to parse the incoming data - i.e. data from url params which are automatically converted to string which needs to be used as an Int/Number.
```js
@Get('/:id')
    async findOne(@Param('id', ParseIntPipe) id: number) {
        const job = await this.jobService.findOne({ id })
        
        return job
    }
```