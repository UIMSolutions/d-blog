+++
title = "Compile-Time-Checks in D mit static assert"
date = 2026-11-19

[extra]
canonical_url = "https://example.org/artikel"
+++

Mit `static assert` lassen sich Invarianten bereits zur Compile-Zeit prüfen:

```d
module example;

template BufferSize(size_t N)
{
    static assert(N > 0 && (N & (N - 1)) == 0, "BufferSize muss eine Zweierpotenz > 0 sein");
    enum BufferSize = N;
}

void main()
{
    enum size = BufferSize!64;
}
