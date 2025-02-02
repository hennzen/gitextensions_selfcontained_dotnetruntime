# Git Extensions portable with self-contained .NET Desktop Runtime
The name says it all.
Read on for more details.

# What is this?
This is a fork of [Git Extensions](https://github.com/gitextensions/gitextensions) but **without** any actual **changes to the code**.
Instead, this replaced `README.md` just explains how I managed to build a self-contained version of the main GUI client - and why.

Head over to Git Extension's [README.md](https://github.com/gitextensions/gitextensions/blob/master/README.md) for the original version.

# Why this fork of Git Extensions?
I needed a way to get Git Extensions working on a **corporate Windows 10 machine without admin rights**.

The [portable version](https://github.com/gitextensions/gitextensions/releases/latest) wasn't enough for my case, because we still need the [.NET Desktop Runtime 8.x](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) for Git Extensions to run.
I found no way to install the .NET Desktop Runtime without admin rights, so I built a self-contained version, which simply means the .NET Desktop Runtime comes bundled with the build - at the cost of quadrupling the application size. Today, this is around 174 MB. Easy, if you are stubborn enough and want to stick with your accustomed git GUI client 🤷‍♂️.

# Setup (on Windows)
Refer to the [original build instructions](https://github.com/gitextensions/gitextensions/wiki/How-To%3A-build-instructions#how-to-build-and-test-on-ms-windows) for details.

In short: install the Windows x64 version of [.NET SDK 8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) as well as MS Visual Studio 2022 Community Edition.

# Build for Windows x64
> [!IMPORTANT]  
> I have no idea what I am talking about! 😉  
> I do frontend development and I have no clue about C# or desktop development in general (yet).  
> What I got by doing the following just perfectly satisfied my need to get a working Git GUI client. I simply don't know (and have not tested!) what parts or plugins of the application might not work.  
> I would be more than happy if someone shed some light on what I am doing here...

In Visual Studio, simply open the terminal and do
```ps
dotnet publish -c Release -r win-x64 --self-contained true
```
On my system, I got a warning about duplicate `apphost.exe` files. I found no solution to the problem and decided to ignore it, as long as the resulting build is working.

Head over to your project's folder and look at `artifacts\Release\bin\GitExtensions\net8.0-windows\win-x64\`. Within, you should find a directory and file structure like this

<details>

<summary>Build dir contents</summary>

```
ConEmu\
Themes\
Translation\
ApplicationInsights.config
GitCommands.dll.config
GitExtensions.dll.config
GitExtUtils.dll.config
Accessibility.dll
AdysTech.CredentialManager.dll
AppInsights.WindowsDesktop.dll
Ben.Demystifier.dll
BugReporter.dll
clretwrc.dll
clrgc.dll
clrjit.dll
ConEmuWinForms.dll
coreclr.dll
D3DCompiler_47_cor3.dll
DirectWriteForwarder.dll
envdte.dll
ExCSS.dll
Git.hub.dll
GitCommands.dll
GitExtensions.dll
GitExtensions.Extensibility.dll
GitExtUtils.dll
GitUI.dll
GitUIPluginInterfaces.dll
hostfxr.dll
hostpolicy.dll
ICSharpCode.TextEditor.dll
Microsoft.AI.DependencyCollector.dll
Microsoft.ApplicationInsights.dll
Microsoft.Bcl.AsyncInterfaces.dll
Microsoft.CSharp.dll
Microsoft.DiaSymReader.Native.amd64.dll
Microsoft.Toolkit.HighPerformance.dll
Microsoft.VisualBasic.dll
Microsoft.VisualBasic.Core.dll
Microsoft.VisualBasic.Forms.dll
Microsoft.VisualStudio.Composition.dll
Microsoft.VisualStudio.Interop.dll
Microsoft.VisualStudio.Threading.dll
Microsoft.VisualStudio.Validation.dll
Microsoft.Win32.Primitives.dll
Microsoft.Win32.Registry.dll
Microsoft.Win32.Registry.AccessControl.dll
Microsoft.Win32.SystemEvents.dll
Microsoft.WindowsAPICodePack.dll
Microsoft.WindowsAPICodePack.Shell.dll
mscordaccore.dll
mscordaccore_amd64_amd64_8.0.23.53103.dll
mscordbi.dll
mscorlib.dll
mscorrc.dll
msquic.dll
netstandard.dll
Newtonsoft.Json.dll
PenImc_cor3.dll
PresentationCore.dll
PresentationFramework.dll
PresentationFramework.Aero.dll
PresentationFramework.Aero2.dll
PresentationFramework.AeroLite.dll
PresentationFramework.Classic.dll
PresentationFramework.Luna.dll
PresentationFramework.Royale.dll
PresentationFramework-SystemCore.dll
PresentationFramework-SystemData.dll
PresentationFramework-SystemDrawing.dll
PresentationFramework-SystemXml.dll
PresentationFramework-SystemXmlLinq.dll
PresentationNative_cor3.dll
PresentationUI.dll
ReachFramework.dll
ResourceManager.dll
RestSharp.dll
SmartFormat.dll
SmartFormat.ZString.dll
SpellChecker.dll
System.dll
System.AppContext.dll
System.Buffers.dll
System.CodeDom.dll
System.Collections.dll
System.Collections.Concurrent.dll
System.Collections.Immutable.dll
System.Collections.NonGeneric.dll
System.Collections.Specialized.dll
System.ComponentModel.dll
System.ComponentModel.Annotations.dll
System.ComponentModel.Composition.dll
System.ComponentModel.DataAnnotations.dll
System.ComponentModel.EventBasedAsync.dll
System.ComponentModel.Primitives.dll
System.ComponentModel.TypeConverter.dll
System.Composition.AttributedModel.dll
System.Composition.Convention.dll
System.Composition.Hosting.dll
System.Composition.Runtime.dll
System.Composition.TypedParts.dll
System.Configuration.dll
System.Configuration.ConfigurationManager.dll
System.Console.dll
System.Core.dll
System.Data.dll
System.Data.Common.dll
System.Data.DataSetExtensions.dll
System.Design.dll
System.Diagnostics.Contracts.dll
System.Diagnostics.Debug.dll
System.Diagnostics.DiagnosticSource.dll
System.Diagnostics.EventLog.dll
System.Diagnostics.EventLog.Messages.dll
System.Diagnostics.FileVersionInfo.dll
System.Diagnostics.PerformanceCounter.dll
System.Diagnostics.Process.dll
System.Diagnostics.StackTrace.dll
System.Diagnostics.TextWriterTraceListener.dll
System.Diagnostics.Tools.dll
System.Diagnostics.TraceSource.dll
System.Diagnostics.Tracing.dll
System.DirectoryServices.dll
System.Drawing.dll
System.Drawing.Common.dll
System.Drawing.Design.dll
System.Drawing.Primitives.dll
System.Dynamic.Runtime.dll
System.Formats.Asn1.dll
System.Formats.Tar.dll
System.Globalization.dll
System.Globalization.Calendars.dll
System.Globalization.Extensions.dll
System.IO.dll
System.IO.Abstractions.dll
System.IO.Compression.dll
System.IO.Compression.Brotli.dll
System.IO.Compression.FileSystem.dll
System.IO.Compression.Native.dll
System.IO.Compression.ZipFile.dll
System.IO.FileSystem.dll
System.IO.FileSystem.AccessControl.dll
System.IO.FileSystem.DriveInfo.dll
System.IO.FileSystem.Primitives.dll
System.IO.FileSystem.Watcher.dll
System.IO.IsolatedStorage.dll
System.IO.MemoryMappedFiles.dll
System.IO.Packaging.dll
System.IO.Pipes.dll
System.IO.Pipes.AccessControl.dll
System.IO.UnmanagedMemoryStream.dll
System.Linq.dll
System.Linq.Expressions.dll
System.Linq.Parallel.dll
System.Linq.Queryable.dll
System.Memory.dll
System.Net.dll
System.Net.Http.dll
System.Net.Http.Json.dll
System.Net.HttpListener.dll
System.Net.Mail.dll
System.Net.NameResolution.dll
System.Net.NetworkInformation.dll
System.Net.Ping.dll
System.Net.Primitives.dll
System.Net.Quic.dll
System.Net.Requests.dll
System.Net.Security.dll
System.Net.ServicePoint.dll
System.Net.Sockets.dll
System.Net.WebClient.dll
System.Net.WebHeaderCollection.dll
System.Net.WebProxy.dll
System.Net.WebSockets.dll
System.Net.WebSockets.Client.dll
System.Numerics.dll
System.Numerics.Vectors.dll
System.ObjectModel.dll
System.Printing.dll
System.Private.CoreLib.dll
System.Private.DataContractSerialization.dll
System.Private.Uri.dll
System.Private.Xml.dll
System.Private.Xml.Linq.dll
System.Reactive.dll
System.Reactive.Interfaces.dll
System.Reactive.Linq.dll
System.Reflection.dll
System.Reflection.DispatchProxy.dll
System.Reflection.Emit.dll
System.Reflection.Emit.ILGeneration.dll
System.Reflection.Emit.Lightweight.dll
System.Reflection.Extensions.dll
System.Reflection.Metadata.dll
System.Reflection.Primitives.dll
System.Reflection.TypeExtensions.dll
System.Resources.Extensions.dll
System.Resources.Reader.dll
System.Resources.ResourceManager.dll
System.Resources.Writer.dll
System.Runtime.dll
System.Runtime.CompilerServices.Unsafe.dll
System.Runtime.CompilerServices.VisualC.dll
System.Runtime.Extensions.dll
System.Runtime.Handles.dll
System.Runtime.InteropServices.dll
System.Runtime.InteropServices.JavaScript.dll
System.Runtime.InteropServices.RuntimeInformation.dll
System.Runtime.Intrinsics.dll
System.Runtime.Loader.dll
System.Runtime.Numerics.dll
System.Runtime.Serialization.dll
System.Runtime.Serialization.Formatters.dll
System.Runtime.Serialization.Json.dll
System.Runtime.Serialization.Primitives.dll
System.Runtime.Serialization.Xml.dll
System.Security.dll
System.Security.AccessControl.dll
System.Security.Claims.dll
System.Security.Cryptography.dll
System.Security.Cryptography.Algorithms.dll
System.Security.Cryptography.Cng.dll
System.Security.Cryptography.Csp.dll
System.Security.Cryptography.Encoding.dll
System.Security.Cryptography.OpenSsl.dll
System.Security.Cryptography.Pkcs.dll
System.Security.Cryptography.Primitives.dll
System.Security.Cryptography.ProtectedData.dll
System.Security.Cryptography.X509Certificates.dll
System.Security.Cryptography.Xml.dll
System.Security.Permissions.dll
System.Security.Principal.dll
System.Security.Principal.Windows.dll
System.Security.SecureString.dll
System.ServiceModel.Web.dll
System.ServiceProcess.dll
System.Text.Encoding.dll
System.Text.Encoding.CodePages.dll
System.Text.Encoding.Extensions.dll
System.Text.Encodings.Web.dll
System.Text.Json.dll
System.Text.RegularExpressions.dll
System.Threading.dll
System.Threading.AccessControl.dll
System.Threading.Channels.dll
System.Threading.Overlapped.dll
System.Threading.Tasks.dll
System.Threading.Tasks.Dataflow.dll
System.Threading.Tasks.Extensions.dll
System.Threading.Tasks.Parallel.dll
System.Threading.Thread.dll
System.Threading.ThreadPool.dll
System.Threading.Timer.dll
System.Transactions.dll
System.Transactions.Local.dll
System.ValueTuple.dll
System.Web.dll
System.Web.HttpUtility.dll
System.Windows.dll
System.Windows.Controls.Ribbon.dll
System.Windows.Extensions.dll
System.Windows.Forms.dll
System.Windows.Forms.Design.dll
System.Windows.Forms.Design.Editors.dll
System.Windows.Forms.Primitives.dll
System.Windows.Input.Manipulations.dll
System.Windows.Presentation.dll
System.Xaml.dll
System.Xml.dll
System.Xml.Linq.dll
System.Xml.ReaderWriter.dll
System.Xml.Serialization.dll
System.Xml.XDocument.dll
System.Xml.XmlDocument.dll
System.Xml.XmlSerializer.dll
System.Xml.XPath.dll
System.Xml.XPath.XDocument.dll
TestableIO.System.IO.Abstractions.dll
TestableIO.System.IO.Abstractions.Wrappers.dll
UIAutomationClient.dll
UIAutomationClientSideProviders.dll
UIAutomationProvider.dll
UIAutomationTypes.dll
vcruntime140_cor3.dll
WindowsBase.dll
WindowsFormsIntegration.dll
wpfgfx_cor3.dll
BugReporter.exe
createdump.exe
GitExtensions.exe
TranslationApp.exe
BugReporter.deps.json
BugReporter.runtimeconfig.json
GitExtensions.deps.json
GitExtensions.runtimeconfig.json
TranslationApp.deps.json
TranslationApp.runtimeconfig.json
ConEmuWinForms.pdb
Git.hub.pdb
ICSharpCode.TextEditor.pdb
SpellChecker.pdb
BugReporter.xml
ConEmuWinForms.xml
GitCommands.xml
GitExtensions.xml
GitExtensions.Extensibility.xml
GitExtUtils.xml
GitUI.xml
GitUIPluginInterfaces.xml
ResourceManager.xml
```

</details>
<br>

Voilà! 🎉 Running the `GitExtensions.exe` now just works on a Windows machine without the .NET Runtime Desktop v8 installed.

# Thanks
Thanks to all the great people making Git Extensions!