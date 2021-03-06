---
title: "CA3076: Insecure XSLT Script Execution"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
  - "multiple"
---
# CA3076: Insecure XSLT Script Execution

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Category|Microsoft.Security|
|Breaking Change|Non Breaking|

## Cause

If you execute Extensible Stylesheets Language Transformations (XSLT) in .NET applications insecurely, the processor may resolve untrusted URI references that could disclose sensitive information to attackers, leading to Denial of Service and Cross-Site attacks. For more information, see [XSLT Security Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## Rule Description

**XSLT** is a World Wide Web Consortium (W3C) standard for transforming XML data. XSLT is typically used to write style sheets to transform XML data to other formats such as HTML, fixed length text, comma-separated text, or a different XML format. Although prohibited by default, you may choose to enable it for your project.

To ensure you're not exposing an attack surface, this rule triggers whenever the XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> receives insecure combination instances of <xref:System.Xml.Xsl.XsltSettings> and <xref:System.Xml.XmlResolver>, which allows malicious script processing.

## How to Fix Violations

- Replace the insecure XsltSettings argument with XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> or with an instance that has disabled document function and script execution.

- Replace the <xref:System.Xml.XmlResolver> argument with null or an <xref:System.Xml.XmlSecureResolver> instance.

## When to Suppress Warnings

Unless you're sure that the input is known to be from a trusted source, do not suppress a rule from this warning.

## Pseudo-code Examples

### Violation&mdash;uses XsltSettings.TrustedXslt

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### Solution&mdash;use XsltSettings.Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### Violation&mdash;document function and script execution not disabled

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### Solution&mdash;disable document function and script execution

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## See also

[XSLT Security Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations)