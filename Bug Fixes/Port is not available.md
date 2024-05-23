#### Issue
This happens when a port is running but the terminal is closed. When we run `yarn dev` again, it will say that the `port <port_number>` is not available.
#### Solution
We need to manually kill the port in the terminal.
Here's how.

1. Run the command in the shell
	`lsof -i :<port_number>`
2. Kill the port
	`sudo kill -9 <port id>`

