---
title: "Dockerizing your projects"
date: 2023-01-28
tags: ["docker", "containerized environment","container image","dockerfile","development workflow","deployment process"]
summary: "Learn how to use Docker."
draft: false
showTableOfContents: true
showEdit: false
showAuthor: true
# externalUrl: "https://www.google.com"
---
{{<lead>}}
In this post I am going to give you a brief introduction to learn how to use Docker.
{{</lead>}}

This post we are using:
- [Ubuntu 20.04 LTS (Focal Fossa)](https://releases.ubuntu.com/focal/): It's a Long-Term Support version released in April 2020 and it will be supported until April 2025 by Ubuntu.

## What is Docker? :pencil2:

Docker is a powerful tool that allows developers to easily create, deploy, and run applications in a containerized environment. Containers are lightweight, portable, and provide a consistent environment for applications to run in, regardless of the underlying infrastructure.
 
Concepts we will be covering in this post:
1. Get started with Docker
2. Create a container image
3. Container management
4. Share container images
5. Other commands

## Setting up Docker :wrench:

To get started with Docker, you first need to install it on your system. You can download the installer for your operating system from the Docker website. 

To download and install Docker, you can use the following commands:
```sh
# Update the apt package index
sudo apt-get update

# Install packages to allow apt to use a repository over HTTPS
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Verify the fingerprint of the key
sudo apt-key fingerprint 0EBFCD88

# Add the stable repository
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

# Update the apt package index
sudo apt-get update

# Install the latest version of Docker CE
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

This code is for **Ubuntu** systems, if you are using a different operating system, you will need to adjust the commands accordingly.

Note that you need to run the commands with root or using `sudo`.

Once installed, you can check that Docker is running correctly by running the command `docker info` or you can also use this command to verify that Docker is installed correctly and running

```sh
sudo docker run hello-world
````
It will download the "hello-world" image from the docker hub and run it in a container.


## Create container image :milky_way:

The next step is to create a container image. A container image is a lightweight, standalone, executable package that contains everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings. You can create a container image by writing a `Dockerfile`, which is a script that contains instructions for building the image.

### Dockerfile example :page_facing_up:
Here is an example `Dockerfile` that creates an image for a simple web server written in **Python**:

```sh
# Use an official Python runtime as the base image
FROM python:3.9-slim-buster

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install the required packages
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code into the container
COPY app.py .

# Expose port 5000 for the web server to listen on
EXPOSE 5000

# Run the command to start the web server
CMD ["python", "app.py"]
```
To build the image, you can run the following command:
```sh
docker build -t my-web-server .
````
This command will use the `Dockerfile` in the current directory (indicated by the `.` at the end of the command) to build the image, and give it the tag "my-web-server".

The **FROM** instruction sets the base image, in this case is [python 3.9](https://peps.python.org/pep-0596/).

The **WORKDIR** instruction sets the working directory in the container.

The **COPY** instruction copies files from the host into the container.

The **RUN** instruction runs a command in the container.

The **EXPOSE** instruction informs Docker that the container listens on the specified network ports at runtime.

The **CMD** instruction specifies the command to be run when a container is started from the image.

You can run the container using the following command:
```sh
docker run -p 5000:5000 my-web-server
```
This command will create and start a new container using the my-web-server image, and map port 5000 on the host to port 5000 in the container.

You can use a `.dockerignore` file to specify files and directories that should be ignored when building the image.

You can check more detail information of the instructions that you can use in a Dockerfile in the [Docker documentation](https://docs.docker.com/engine/reference/builder/).

## Container management :computer:

Once you have an image, you can use the `docker run` command to start a container. The `docker run` command takes the image and creates a new container from it. You can use the `-d` option to run the container in detached mode, which means it will run in the background and you can continue to use the command line.

To manage your containers, you can use the `docker ps` command to see a list of running containers. You can use the `docker stop` command to stop a container, and the `docker start` command to start it again.

You can also use the docker logs command to see the logs of a container, and the docker exec command to run a command inside a running container.

## Share containers :rocket:

To share your container images with others, you can push them to a container registry, such as **Docker Hub**. You can use the `docker push` command to push an image to a registry, and the `docker pull` command to pull an image from a registry.

## Other commands :space_invader:

- After creating dockerfile you can build the **image** using: `docker build --platform linux/x86_64 -t image_name:latest ./`
- Save **image** (it will save it as `.tar`file): `docker save -o name.tar image_name:latest` or `docker export -o name.tar image_name:latest`
- To download docker **image** in local machine: `docker load < name.tar` or `docker import < name.tar`
- To access and navigate in docker **container**: `docker exec -it mycontainer /bin/bash`
- Navigate in docker **image**: `docker run -it myimage /bin/bash`
- Remove **image** from terminal: `docker rmi img_name`
- Stop and remove **container**: `docker stop container_name` & `docker rm container_name`
- Remove all build cache: `docker builder prune`

## Conclusions :bulb:
In conclusion, Docker is a powerful tool that allows developers to easily create, deploy, and run applications in a containerized environment. It makes it easy to manage, deploy and share your applications. By learning how to use Docker, you can improve the efficiency and portability of your development workflow and streamline your deployment process.

## References :books:
- [Docker documentation](https://docs.docker.com/reference/)


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