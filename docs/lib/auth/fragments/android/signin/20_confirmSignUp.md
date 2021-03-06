<amplify-block-switcher>
<amplify-block name="Java">

```java
Amplify.Auth.confirmSignUp(
    "username",
    "the code you received via email",
    result -> Log.i("AuthQuickstart", result.isSignUpComplete() ? "Confirm signUp succeeded" : "Confirm sign up not complete"),
    error -> Log.e("AuthQuickstart", error.toString())
);
```

</amplify-block>
<amplify-block name="Kotlin - Callbacks">

```kotlin
Amplify.Auth.confirmSignUp(
    "username", "the code you received via email",
    { result ->
        if (result.isSignUpComplete) {
            Log.i("AuthQuickstart", "Confirm signUp succeeded")
        } else {
            Log.i("AuthQuickstart","Confirm sign up not complete")
        }
    },
    { Log.e("AuthQuickstart", "Failed to confirm sign up", it) }
)
```

</amplify-block>
<amplify-block name="Kotlin - Coroutines (Beta)">

```kotlin
try {
    val code = "code you received via email"
    val result = Amplify.Auth.confirmSignUp("username", code)
    if (result.isSignUpComplete) {
        Log.i("AuthQuickstart", "Signup confirmed")
    } else {
        Log.i("AuthQuickstart", "Signup confirmation not yet complete")
    }
} catch (error: AuthException) {
    Log.e("AuthQuickstart", "Failed to confirm signup", error)
}
```

</amplify-block>
<amplify-block name="RxJava">

```java
RxAmplify.Auth.confirmSignUp("username", "the code you received via email")
    .subscribe(
        result -> Log.i("AuthQuickstart", result.isSignUpComplete() ? "Confirm signUp succeeded" : "Confirm sign up not complete"),
        error -> Log.e("AuthQuickstart", error.toString())
    );
```

</amplify-block>
</amplify-block-switcher>
