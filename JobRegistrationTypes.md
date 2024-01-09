```js
import { z } from 'zod';

export const CustomerRegistrationSchema = z.object({
    firstName: z.string().min(5, {message: "Must be at least 5 characters"}),
    lastName: z.string().min(5, {message: "Must be at least 5 characters"}),
    email: z.string().email(),
    contact: z.string(),
    address: z.string(),
});

export const JobInformationSchema = z.object({
    title: z.string(),
    type: z.string(),
    tags: z.string(),
    remarks: z.string(),
    paymentMethod: z.string(),
});

const MomentSchema = z.union([z.null(), z.instanceof(Date)]);

export const WorkScheduleSchema = z.object({
    startDate: MomentSchema.optional(),
    startTime: MomentSchema.optional(),
    endDate: MomentSchema.optional(),
    endTime: MomentSchema.optional(),
});

export const JobWithCustomerAndSchedulesSchema = z.object({
    customer_registration: CustomerRegistrationSchema,
    job_information: JobInformationSchema,
    schedules: z.array(WorkScheduleSchema),
});


export type CustomerRegistration = z.infer<typeof CustomerRegistrationSchema>;
export type JobInformation = z.infer<typeof JobInformationSchema>;
export type WorkSchedule = z.infer<typeof WorkScheduleSchema>;
export type JobWithCustomerAndSchedules = z.infer<typeof JobWithCustomerAndSchedulesSchema>;

```