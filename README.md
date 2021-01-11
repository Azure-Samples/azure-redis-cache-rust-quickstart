# Quickstart: Use Azure Cache for Redis with Rust

This sample shows how you can use the [Rust programming language](https://www.rust-lang.org/) for interacting with [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview?WT.mc_id=data-12577-abhishgu). It will demonstrate examples of commonly used Redis data structures such as STRING, HASH, LIST etc. using the [redis-rs](https://github.com/mitsuhiko/redis-rs) library for Redis. This client exposes both high and low-level APIs and you will see both these styles in action.

## Pre-requisites

- Azure subscription - [create one for free](https://azure.microsoft.com/free/)
- [Rust](https://www.rust-lang.org/tools/install) (version 1.39 or above)
- [Git](https://git-scm.com/downloads)

## Clone the sample application

Start by cloning the application from GitHub.

1. Open a command prompt and create a new folder named `git-samples`.

    ```bash
    md "C:\git-samples"
    ```

1. Open a git terminal window, such as git bash. Use the `cd` command to change into the new folder where you will be cloning the sample app.

    ```bash
    cd "C:\git-samples"
    ```

1. Run the following command to clone the sample repository. This command creates a copy of the sample app on your computer.

    ```bash
    git clone https://github.com/Azure-Samples/azure-redis-cache-rust-quickstart.git
    ```

## Run the application

The application accepts connectivity and credentials in the form of environment variables. 

1. Fetch the **Host name** and **Access Keys** (available via Access Keys) for Azure Cache for Redis instance in the [Azure portal](https://portal.azure.com/)

1. Set them to the respective environment variables:

    ```shell
    set REDIS_HOSTNAME=<Host name>:<port> (e.g. <name of cache>.redis.cache.windows.net:6380)
    set REDIS_PASSWORD=<Primary Access Key>
    ```

1. In the terminal window, change to the correct folder. For example:

    ```shell
    cd "C:\git-samples\azure-redis-cache-rust-quickstart"
    ```

1. In the terminal, run the following command to start the application.

    ```shell
    cargo run
    ```
    
    You will see an output as such:
    
    ```bash
    ******* Running SET, GET, INCR commands *******
    value for 'foo' = bar
    counter = 2
    ******* Running HASH commands *******
    info for rust redis driver: {"name": "redis-rs", "repo": "https://github.com/mitsuhiko/redis-rs", "version": "0.19.0"}
    go redis driver repo name: "https://github.com/go-redis/redis"
    ******* Running LIST commands *******
    first item: item-1
    no. of items in list = 2
    listing items in list
    item: item-2
    item: item-3
    ******* Running SET commands *******
    does user1 exist in the set? true
    listing users in set
    user: user2
    user: user1
    user: user3
    ******* Running SORTED SET commands *******
    listing players and scores
    player-2 = 2
    player-4 = 4
    player-1 = 7
    player-5 = 6
    player-3 = 8
    ```
    
    If you want to run a specific function, comment out other functions in the `main` function:
    
    ```rust
    fn main() {
        basics();
        hash();
        list();
        set();
        sorted_set();
    }
    ```

## Resources

- [Best practices for Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-best-practices?WT.mc_id=data-12577-abhishgu)
- [Caching architectures](https://docs.microsoft.com/azure/architecture/best-practices/caching?toc=%2fazure%2fredis-cache%2ftoc.json&WT.mc_id=data-12577-abhishgu)
- [High availability for Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-high-availability?WT.mc_id=data-12577-abhishgu)
