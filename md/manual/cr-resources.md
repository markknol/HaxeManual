## 8.3 Resources

Haxe provides simple resource embedding system that can be used for embedding  files directly into the compiled application.

While it may be not optimal to embed large assets, like images or music in the application file, it comes in very handy to embed smaller resources, like configuration or XML data.

### 8.3.1 Embedding resources

External files are embedded using the **-resource** compiler argument:


```haxe
-resource hello_message.txt@welcome
```

The string after the **@** symbol is the **resource identifier**. It will used in the code for retrieving the resource. It can be omitted (together with the **@** symbol), then the file name will become a resource identifier.

### 8.3.2 Retrieving text resources

To retrieve the content of an embedded resource, we use the static method **getString** of `haxe.Resource` passing a **resource identifier** to it:

```haxe
class Main {
    static function main() {
        trace(haxe.Resource.getString("welcome"));
    }
}

```

The code above will display the content of the **hello_message.txt** file that we included earlier using **welcome** as the identifier.

### 8.3.3 Retrieving binary resources

While it's not recommended to embed large binary files in the application, it still may be useful to embed binary data. Binary representation of an embedded resource can be accessed using the static method **getBytes** of `haxe.Resource`:

```haxe
class Main {
    static function main() {
        var bytes = haxe.Resource.getBytes("welcome");
        trace(bytes.readString(0, bytes.length));
    }
}

```

The return type of **getBytes** method is `haxe.io.Bytes`, an object providing access to individual bytes of the data.

### 8.3.4 Implementation details

Haxe uses target platform's native resource embedding, if there is one, providing its own implementation otherwise.



* **Flash** resources are embedded as ByteArray definitions
* **C#** resources are included in the compiled assembly
* **Java** resources are packed in the resulting JAR file
* **C++** resources are stored in global byte array constants.
* **JavaScript** resources are serialized in Haxe serialization format and stored in a static field of `haxe.Resource` class.
* **Neko** resources are stored as strings in a static field of `haxe.Resource` class.

---

Previous section: [Completion](#)

Next section: [Macros](macro.md)

Contribute: [fileAndLines](https://github.com/HaxeFoundation/HaxeManual/blob/master/08-compiler-features.tex#L51-51)