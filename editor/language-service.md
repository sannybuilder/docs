# Language Service

**Language service** is one of the Sanny Builder features providing rich developer experience. It's responsible for continuous mining data out of the opened document and all imported files. It's important to know that the mining works in a separate thread and does not immediately reflect what you've just typed. There could be a noticeable delay while the language service reacts on a document change. If, for some reason, it distracts you, or you're not satisfied with the service performance you can disable it in the [options](options/editor.md#editor-configuration).

For better responsiveness the language service only scans a slice of the current document prior to the active line, not the entire file. This is controlled by the [Scanning range](options/editor.md#code-scan-distance) value set in the Editor options. The higher the value the more lines the service scans and the more symbols it finds, but it also increases the time that is necessary for the editor to reflect the changes made in the document. If you have a less powerful workstation consider using the default value of `250` lines.

Since v3.7.0 the language service is capable of finding [defined constants](../coding/constants.md#syntax) and their values. This information then becomes available to the editor for [highlighting purposes]() and for [displaying values](features.md#displaying-information-about-opcode) of constants.

```text
const
    x = 10
end

x // x gets highlighted
```

The syntax highlighter offers two ways of colorizing constants:

* highlight all constants using the same set of rules
* apply the rules that would otherwise be applied to the constant value \("semantic highlighting"\)

With semantic highlighting enabled and given the example above `x` would get colorized as a regular number \(the maroon color by default\).

The language service also serves as the data provider for the autocomplete feature when you press `Ctrl+Space`. It renders a list of constants and their values. When the language service is disabled, no constants are being displayed in the list.

{% hint style="info" %}
Read more technical details on the service implementation there:

* [Notes on constants highlighting. Part 1/2](https://www.patreon.com/posts/45844911)
* [Notes on constants highlighting. Part 2/2](https://www.patreon.com/posts/46873773)
{% endhint %}

