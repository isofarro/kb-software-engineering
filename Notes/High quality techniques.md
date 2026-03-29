
## Result tuples instead of exceptions

Similar to functional Scala's left/right tuple, and Go's error handling. Means returning meaningful structured error messages, supporting returning rich metadata. Checking for the presence of an error

```typescript
type Success<T> = ?;
type Failure<E> = ?;
type Result<T,E> = Success<T> | Failure<E>;

type UpdateCompleted = boolean;
type UpdateError = SystemError & { canRetry: boolean }
...

const handleUpdate = (): Result<UpdateCompleted, UpdateError> => {
	...
	if (hasErrors) {
		const error: UpdateError = {...};
		return Failure(error);
	}
	...
	return Success(true);
} 

...

const [updateError, success] = handleUpdate(user);

if (updateError) {
	...
	return;
}

// Otherwise success
```