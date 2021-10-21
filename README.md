# Chrome CPU Issue Reproduction

Steps to reproduce:

1. Open Activity monitor
2. Load this unpacked extension into chrome.
3. Open 25 tabs of a resource-heavy google doc (including tables, images, at least 20 pages)
4. Watch CPU usage of chrome spike to 250-350%
5. Go to chrome://extensions and disable the extension
6. CPU usage should quickly drop to around 100-150%

Issue originates from this call in the content script:

`chrome.runtime.connect({ name: 'extensionUIRequest' });`

which get's run on every tab.
