# Comments

Comments start with the double slash `//`. Everything after `//` to the end of the line is ignored by the compiler.

To comment out multiple lines or a part of the line, use block comments `{}`:

```text
0001: wait  {comments here} 0 ms
```

Since version 3.06 Sanny Builder also supports the C++-like comments `/* */`.

```text
0001: wait  /* comments here */ 0 ms
```

To comment out or uncomment multiple selected lines of the code press `Ctrl+Q` \(this hotkey is configurable in the [options](../editor/options/hotkeys.md)\).

