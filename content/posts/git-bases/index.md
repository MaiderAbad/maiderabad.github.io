---
title: "Git Essentials: A Beginner's Guide"
date: 2024-04-25
tags: ["Git", "version control","software development","repository","branching","merge"]
summary: "Learn how to use Git."
draft: false
showTableOfContents: true
showEdit: false
showAuthor: true
# externalUrl: "https://www.google.com"
---
{{<lead>}}
In the realm of software development, version control is paramount for maintaining an organized, collaborative, and efficient workflow. Among the various tools available, Git stands out as one of the most popular and powerful. In this guide, I'll introduce you to the basics of Git and how you can start using it in your projects.
{{</lead>}}

This post we are using:
- [Ubuntu 20.04 LTS (Focal Fossa)](https://releases.ubuntu.com/focal/): It's a Long-Term Support version released in April 2020 and it will be supported until April 2025 by Ubuntu.

## What is Docker? :pencil2:

Git is a distributed version control system, designed to track changes in files and coordinate work among multiple people in software development projects. It was created by Linus Torvalds in 2005 and has since become the preferred choice for developers worldwide.

## Why Should You Use Git? :wrench:

1. **Change History:** Git records every modification made in a project, allowing you to revert to previous versions if needed.
2. **Seamless Collaboration:** It enables multiple people to work on the same project simultaneously, easily merging changes.
3. **Branching:** You can create independent branches to experiment with new features without affecting the main project branch.
4. **Remote Repositories:** Facilitates collaboration with other developers by allowing you to share your code in remote repositories such as GitHub or GitLab.

## Getting Started with Git :rocket:

1. **Installation:** If you don't have Git installed on your system yet, you can download it from [git-scm.com](https://git-scm.com/). Follow the installation instructions for your operating system.

2. **Initial Configuration:** Once installed, configure your username and email address in Git. This will be used to identify your contributions to projects.

```sh
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```
3. **Initialize a Repository:** Navigate to your project directory in the command line and run the following command to initiate a new Git repository.

```sh
git init
```
4. **Add Files:** Use the `git add` command to add files to the staging area before committing changes.

```sh
git add file1 file2
```
5. **Commit Changes:** Once you've added the files you want to include in the next commit, use the `git commit` command to save the changes to the repository.

```sh
git commit -m "Descriptive message of the changes"
```

6. **Create a Branch:** You can create a new branch to work on a new feature or fix a bug without affecting the main project branch.

```sh
git branch branch_name
```
7. **Switch Branches:** Use the git checkout command to switch between existing branches.

```sh
git checkout branch_name
```
8. **Merge Branches:** When you've completed work on a branch and are ready to incorporate the changes into the main branch, use the `git merge` command.

```sh
git merge branch_name
```
9. **Remote Repositories:** To collaborate with other developers, you can add a remote repository using the `git remote add` command.

```sh
git remote add origin repository_url
```
10. **Push Changes:** Once you've committed your changes locally, you can push them to the remote repository using the `git push` command.

```sh
git push origin branch_name
```

This code is for **Ubuntu** systems, if you are using a different operating system, you will need to adjust the commands accordingly.

## Conclusions :bulb:
Git is a powerful tool that can significantly improve your workflow as a software developer. While these are just the basics, I encourage you to explore its features and commands further to make the most out of its potential. 

## References :books:
- [Git documentation](https://docs.github.com/en)


<!--
## Others
To use **dio**, you need to add it to your `pubspec.yaml` file:

```yaml
dependencies:
  dio: ^4.0.6
  dio_smart_retry: ^1.3.2 # optional
  pretty_dio_logger: ^1.1.1 # optional
```

The `dio_smart_try` and `pretty_dio_logger` packages are optional, but I'll be using them in this post, it's an **easy way to log the requests and responses** and to **retry failed requests**, but we will make our own retry interceptor for the refresh token part.<br>
I also make use of `flutter_appauth` and `flutter_secure_storage` in the example found in the [repo](https://github.com/cgutierr-zgz/dio-intercetors-loggers).

## Making our custom dio client :rocket:

To make a request, you need to create a `Dio` instance and use the `get` method to make a `GET` request:

```dart
final dio = Dio();

final response = await dio.get<dynamic>(
  'https://jsonplaceholder.typicode.com/todos/1',
);


print(response.data);
```

Let's now create a custom `Dio` client that we can use in our app:

```dart
class DioClient extends DioForNative {
  DioClient({
    List<Interceptor>? interceptors,
    BaseOptions? options,
    int timeOutInMilliseconds = 30 * 1000,
  }) : super(
          options ??
              BaseOptions(
                connectTimeout: timeOutInMilliseconds,
                sendTimeout: timeOutInMilliseconds,
                receiveTimeout: timeOutInMilliseconds,
              ),
        );
}
```

Now we could simply use a new `DioClient` instance instence of the `Dio` in the example above.


## Interceptors :chains:

Let's now add some interceptors to our `DioClient`:

```dart
class DioClient extends DioForNative {
  DioClient(/*...*/) : super(/*...*/) {
    this.interceptors.addAll(
      [
        // Whatever interceptors you want to add from the constructor
        ...?interceptors,
      ],
    );
  }
}
```

That's just adding the interceptors passed in the constructor to the `interceptors` list of the `Dio` instance.
Let's now have a look at the interceptors we will be using in this post.

### Logger interceptor :scroll:

The `PrettyDioLogger` is a simple interceptor that logs the requests and responses to the console, if you don't want to use it you can make your own logger interceptor making use of the LogInterceptor class, here I'll show you how to add both, choose the one you prefer.

```dart
// ...
this.interceptors.addAll(
  [
    // ... previously added interceptors

    // Optionally add network Logger interceptor only for debug mode
    if (kDebugMode) ...[
	  // 1. PrettyDioLogger
      PrettyDioLogger(
        requestBody: true,
        responseBody: true,
        // ... other options
        requestHeader: false,
        responseHeader: false,
        error: false,
        request: false,
      ),

	  // 2. LogInterceptor
      LogInterceptor(
        requestBody: true,
        responseBody: true,
        // ... other options
        requestHeader: false,
        responseHeader: false,
        error: false,
        request: false,
        logPrint: (log) {
		  // Customice to your liking
          if (log.toString().isEmpty) return;
          debugPrint('🌐 ${log.toString()}');
        },
      ),
    ],
  ],
);
// ...
```

How does it look like in the console?

<b>PrettyDioLogger output:</b>
![custom dio logger](thumb.jpeg)


<b>LogInterceptor output:</b>
![custom dio logger](thumb.jpeg)

### Retry interceptor :repeat:

The `RetryInterceptor` is a simple interceptor that retries failed requests, there's not much to it, you can pass the number of retries you want to make and the `Dio` instance will retry the request that many times.


```dart
// ...
this.interceptors.addAll(
  [
    // ... previously added interceptors

	// RetryInterceptor -- has some more options, check the docs
    RetryInterceptor(dio: this, logPrint: print), 
  ],
);
// ...
```

### Token and Refresh Token interceptor :key:

I don't really know an out-of-the-box solution, so I'll be making my own interceptor to handle this.<br>
In the `AuthRepository` class we will be using the `flutter_appauth` package to authenticate the user and the `flutter_secure_storage` package to store the tokens, you can read more about the implementation in the [repo](https://github.com/cgutierr-zgz/dio-intercetors-loggers), take it as an example the repo does not have a complete implementation, it's just an example.<br>
The `AuthRepository` class will be used to authenticate the user and to refresh the token when it expires. To do so, we will add a new `InterceptorsWrapper` to the `DioClient` directly inside the `AuthRepository` class.<br>
This wrapper will have two main methods, the `onRequest` method will be called before the request is sent to the server, and the `onError` method will be called before the response is returned to the caller.

```dart

class AuthRepository {
  AuthRepository({
    required AuthProvider authProvider,
    required FlutterSecureStorage flutterSecureStorage,
  }) {
    _authProvider = authProvider;
    _secureStorage = flutterSecureStorage;

    final client = authProvider.client;
    client.interceptors.add(
      InterceptorsWrapper(
        onRequest: (request, handler) async {
        },
        onError: (e, handler) async {
        },
      ),
    );
  }

  late final AuthProvider _authProvider;
  late final FlutterSecureStorage _secureStorage;
  // ...

  // Implementation of the signIn, checkSession, refreshToken, signOut, deleteTokens, etc...
  // Please, refer to the repo for more info about the implementation
}
```

The `onRequest` method will be used to add the `Authorization` header to the request, and the `onError` method will be used to refresh the token when it expires.<br>
Let's now have a look at the implementation of the `onRequest` method:

```dart
onRequest: (request, handler) async {
  // We add the accessToken to the headers if it's not null
  final accessToken = await _secureStorage.read(key: _accessTokenKey);

  if (accessToken != null) {
    request.headers['Authorization'] = 'Bearer $accessToken';
  }
  debugPrint('[DIO]: Added accessToken [${accessToken != null}]');

  return handler.next(request);
},
```

Here we basically get the `accessToken` from the `FlutterSecureStorage` and add it to the request headers if it's not null, then we call the `handler.next(request)` method to continue with the request.<br>
Like this we do not have to add the `Authorization` header to every request we make, we just have to add the `DioClient` instance to the `AuthProvider` class and we are good to go :smile:

---

Now let's have a look at the implementation of the `onError` method:

```dart
onError: (e, handler) async {
  // If the statuscode is 401 we try to refresh the token
  if (e.response?.statusCode == 401) {
    // We refresh the token
    await refreshTokens();
    // We add the accessToken to the headers if it's not null
    final accessToken = await _secureStorage.read(
      key: _accessTokenKey,
    );
    if (accessToken != null) {
      debugPrint('[DIO]: Refreshed Tokens');
      e.requestOptions.headers['Authorization'] = 'Bearer $accessToken';

      // Create request with new access token
      final opts = Options(
        method: e.requestOptions.method,
        headers: e.requestOptions.headers,
      );
      final cloneReq = await client.request<void>(
        e.requestOptions.path,
        options: opts,
        data: e.requestOptions.data,
        queryParameters: e.requestOptions.queryParameters,
      );

      return handler.resolve(cloneReq);
    }

    debugPrint("[DIO]: Couldn't refresh Tokens");
  }
},
```

Here we check if the status code of the response is 401, which, for our case, means that the token has expired, then we call the `refreshTokens` method to refresh the token, and we add the new `accessToken` to the request headers, then we create a new request with the new `accessToken` and we return the response to the caller.<br>

Voilà, now we have a working interceptor that not only refreshes the token when it expires, but also adds the `accessToken` to the request headers, so we don't have to :tada:

## Conclusion :memo:

In this post, I introduced you to the `Dio` package, I showed you how to use it to make HTTP requests, and I showed you how to use interceptors to add custom logic to the requests.<br>
Take this as an introduction to the `Dio` package, there's a lot more to it, you can check the [docs](https://pub.dev/packages/dio) for more info.<br>

I hope you enjoyed it and that you found it useful.<br>
If you have any questions or suggestions, feel free to **leave a comment** below. :smile:<br>
Thanks for reading! :nerd_face:

The full **source code** with for this post is available [here](https://github.com/cgutierr-zgz/dio-intercetors-loggers) :mag:<br>

The **pubspec.yaml** file for this project uses the following dependencies :package:

```yaml
dependencies:
  dio: ^4.0.6 # To make HTTP requests and to use the interceptors I created
  dio_smart_retry: ^1.3.2 # Easy way to add retry logic to the requests
  flutter:
    sdk: flutter
  flutter_appauth: ^4.2.1 # Used to authenticate the user and to refresh the token
  flutter_secure_storage: ^6.0.0 # Used to store the tokens in the secure storage
  pretty_dio_logger: ^1.1.1 # For logging the requests

dev_dependencies:
  flutter_test:
    sdk: flutter
  mocktail: ^0.3.0 # For mocking
  very_good_analysis: ^3.1.0 # Used to enforce very good practices 🦄
```

## References :books:

- [dio](https://pub.dev/packages/dio)
- [dio_smart_retry](https://pub.dev/packages/dio_smart_retry)
- [pretty_dio_logger](https://pub.dev/packages/pretty_dio_logger)
- [flutter_appauth](https://pub.dev/packages/flutter_appauth)
- [flutter_secure_storage](https://pub.dev/packages/flutter_secure_storage)
-->