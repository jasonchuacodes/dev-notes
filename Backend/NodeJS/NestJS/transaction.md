#### Purpose

#### Usage
```js
async createProject() {
	const transaction = await this.prisma.$transaction(async () => {
		// Job 1
		const customer = await this.createCustomer(...)

		// Job 2
		const job = await this.prisma.job.create(...)

		// Job 3
		if (schedules.length > 1) {
			schedules.forEach(async schedule => {
				await this.createSchedules(...)
			});
		}

		return job
	})
	return transaction;
}
```