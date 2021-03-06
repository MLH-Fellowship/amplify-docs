<amplify-block-switcher>
<amplify-block name="Java">

```java
Amplify.DataStore.query(Post.class, Where.id("123"),
    match -> {
        if (match.hasNext()) {
            Post post = match.next();
            Amplify.DataStore.delete(post,
                deleted -> Log.i("MyAmplifyApp", "Post deleted."),
                failure -> Log.e("MyAmplifyApp", "Delete failed.", failure)
            );
        }
    },
    failure -> Log.e("MyAmplifyApp", "Query failed.", failure)
);
```

</amplify-block>
<amplify-block name="Kotlin - Callbacks">

```kotlin
Amplify.DataStore.query(Post::class.java, Where.id("123"),
    {
        if (it.hasNext()) {
            val post = it.next()
            Amplify.DataStore.delete(post,
                { Log.i("MyAmplifyApp", "Post deleted") },
                { Log.e("MyAmplifyApp", "Delete failed") }
            )
        }
    },
    { Log.e("MyAmplifyApp", "Query failed", it) }
)
```

</amplify-block>
<amplify-block name="Kotlin - Coroutines (Beta)">

```kotlin
Amplify.DataStore.query(Post::class, Where.id("123"))
    .catch { Log.e("MyAmplifyApp", "Query failed", it) }
    .onEach { Amplify.DataStore.delete(it) }
    .catch { Log.e("MyAmplifyApp", "Delete failed", it) }
    .collect { Log.i("MyAmplifyApp", "Post deleted") }
```

</amplify-block>
<amplify-block name="RxJava">

```java
RxAmplify.DataStore.query(Post.class, Where.id("123"))
    .flatMapCompletable(RxAmplify.DataStore::delete)
    .subscribe(
        () -> Log.i("MyAmplifyApp", "Post deleted."),
        failure -> Log.e("MyAmplifyApp", "Delete failed.", failure)
    );
```

</amplify-block>
</amplify-block-switcher>
