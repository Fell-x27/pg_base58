## Installation and Usage

pg_base58 supports PostgreSQL 15 through 19 and requires Rust 1.99.1 or later.

### 1. Install Rust

As first, you will need to install some dependencies:
#### For Debian-based systems:

```bash
sudo apt update && sudo apt install libclang-dev clang git curl
```

#### For RHEL-based systems:

```bash
sudo yum makecache && sudo yum install clang clang-devel git curl
```

Then, ensure that Rust is installed on your system. Use the following command to install Rust:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### 2. Install PostgreSQL Dependencies

You will need certain packages to build PostgreSQL and its extensions:

#### For Debian-based systems:

```bash
sudo apt-get install build-essential libreadline-dev zlib1g-dev flex bison libxml2-dev libxslt-dev libssl-dev libxml2-utils xsltproc ccache pkg-config
```

#### For RHEL-based systems:

```bash
sudo yum install -y bison-devel readline-devel zlib-devel openssl-devel wget ccache && sudo yum groupinstall -y 'Development Tools'
```

### 3. Clone the Repository and install dependencies

```bash
git clone https://github.com/Fell-x27/pg_base58.git
cd pg_base58
cargo install cargo-pgrx --version 0.20.1 --locked
cargo pgrx init
```

### 4. Build the Extension

Inside the project directory build the extension using the following command:

```bash
cargo pgrx package
```

### 5. Install the Extension

To install the extension, run:

```bash
cargo pgrx install --no-default-features --release --sudo
```

### 6. Create the Extension in PostgreSQL

Once the extension is installed, you need to create it in your PostgreSQL database:

```sql
CREATE EXTENSION IF NOT EXISTS pg_base58;
```

### 7. Using the Extension

After the extension is successfully created, you can start using the `base58_encode` and `base58_decode` functions.

**Encode a string to Base58:**

```sql
SELECT base58_encode('hello'::bytea);
```

**Decode a Base58 string back to its original form:**

```sql
SELECT base58_decode('Cn8eVZg');
```
