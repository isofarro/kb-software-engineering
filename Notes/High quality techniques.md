
## Result tuples instead of exceptions

Similar to functional Scala's left/right tuple, and Go's error handling. Means returning meaningful structured error messages, supporting returning rich metadata. Checking for the presence of an error

```typescript
type Success = ?;
type Failure = ?;
type Result = Success | Failure;

...

const [updateError, success] = handleUpdate(user);

if (updateError) {
	...
	return;
}
```