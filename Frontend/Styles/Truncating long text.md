#### What it does:
- truncates long sentences into an ellipsis if it exceeds the width of the display box.
- breaks words if it is very very long and exceeds the width of the display box

How is this technique different from the usual `overflow:hidden + textOverflow: ellipsis` truncation technique?

- can set how many lines there will be for the truncated text (not just a single line)
```js
<Typography
  sx={{
	pr: 1,
	overflow: 'hidden',
	display: '-webkit-box',
	WebkitBoxOrient: 'vertical',
	wordBreak: 'break-all',
	WebkitLineClamp: 2,
  }}
>
  {progressInvoiceDetail.title}
</Typography>
```