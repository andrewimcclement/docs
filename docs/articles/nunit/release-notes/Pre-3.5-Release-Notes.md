---
uid: pre35releasenotes
---

# Pre 3.5 Release Notes

> [!NOTE]
> Combined Release Notes for the NUnit framework, console and engine, up to version 3.5. For later releases, see:
>
> * [Framework Release Notes](framework.md)
> * [Console Release Notes](xref:consoleenginereleasenotes)

## NUnit 3.5 -  October 3, 2016

This is the last version of NUnit where the framework, console runner, engine and extensions are being
released together. From this point forward, the NUnit Framework will be
released on its own schedule that is not bound to that of any other NUnit project and version numbers
may diverge over time.

This is also the first release where the NUnit Framework will not be included in the installer. Only
the console runner, engine and extensions will be available as an MSI installer. We recommend that you
use the NUnit NuGet packages for the framework, but a ZIP file with the binaries will also be available.

### Framework

* Added Assert.Zero and Assert.NotZero methods
* You can now pass a `Func<string>` to Asserts to lazily evaluate exception messages
* Added the ability to Assert on the order of multiple properties in a collection
* Tests with a Timeout will no longer timeout while you are debugging

#### Issues Resolved

* 144 Pass a `Func<string>` to lazily evaluate an exception message
* 995 Enable Warning as Error
* 1106 Move various Assembly Info files under Properties for CF
* 1334 Add Assert.Zero and Assert.NotZero
* 1479 Don't enforce [Timeout] when debugger is attached
* 1540 Remove old .NET Core Projects
* 1553 Allow ordering tests to be done in multiple properties
* 1575 Escaping control chars in custom message
* 1596 Eliminate code sharing across projects to be split
* 1598 Split framework and console/engine into separate projects
* 1610 Refactor dependencies in build.cake
* 1615 AppVeyor error in TestCF
* 1621 Remove console and command-line option files from common
* 1640 When submitting only part of optional parameters, all are overridden by defaults
* 1641 Create OSX CI Build on Travis
* 1663 Find way to hide NUnit.Compatibility.Path from intellisense
* 1681 NUnitLite under .net core doesn't support TeamCity output
* 1683 Existence of SerializableAttribute in .NET Core
* 1693 2 unit tests fail due to localization
* 1716 Move installer to new repository
* 1717 Change suffix for master builds
* 1723 Remove Cake target TestAll
* 1739 Create separate copies of MockAssembly for framework, engine and extensions
* 1751 Serializable attribute exists in both System.Runtime.Serialization.Formatters and nunit.framework
* 1775 Support NUnit assertions in partial trust code.
* 1800 Remove Console/Engine projects from nunit.linux.sln
* 1805 Error message "arguments provided for method not taking any" seems incomplete / doesn't make much sense
* 1815 Prevent NullReferenceException in SubPathConstraint

## NUnit 3.4.1 - June 30, 2016

### Console Runner

* A new option, --list-extensions, will display all the engine extensions that
   have been installed by the engine.

### Issues Resolved

* 1623 NUnit 3.4 is not integrated with TeamCity
* 1626 NUnit.ConsoleRunner is not picking up NUnit.Extension.NUnitV2ResultWriter
* 1628 Agent's process stays in memory when it was failed to unload AppDomain
* 1635 Console option to list loaded extensions

## NUnit 3.4 - June 25, 2016

### Framework

* Improvements in comparing equality using `IEquatable<T>`
* Test case names will only be truncated if the runner requests it or it is overridden on the command line
   with the --test-name-format option
* The .NET 2.0 version of the framework now includes LINQ. If your tests target .NET 2.0, you can now use
   LINQ queries in your tests

### Engine

* The TeamCity event listener has been separated out into an engine extension
* Fixed numerous issues around thread safety of parallel test runs
* Additional fixes to reduce memory usage
* Fixes for Mono 4.4

### Console Runner

* There is a new --params command line option that allows you to pass parameters to your tests
   which can be retrieved using TestContext.Parameters
* Another new command line option `--loaduserprofile` causes the User Profile to be loaded into the
   NUnit Agent process.

#### Issues Resolved

* 329 (CLI) Runner does not report AppDomain unloading timeout
* 720 Need a way to get test-specific command-line arguments at runtime
* 1010 Need to control engine use of extensions
* 1139 NUnit3 console doesn't show test output continuously
* 1225 The --teamcity option should really be an extension
* 1241 Make TestDirectory accessible when TestCaseSource attributes are evaluated
* 1366 Classname for inherited test is not correct
* 1371 Support `dotnet test` in .NET CLI and .NET Core
* 1379 Console returns 0 for invalid fixtures
* 1422 Include TestListWithEmptyLine.tst in ZIP Package
* 1423 SingleThreaded attribute should raise an error if a thread is required
* 1425 Lazy initialization of OutWriter in TestResult is not thread safe
* 1427 Engine extensions load old packages
* 1430 TestObjects are retained for lifetime of test run, causing high memory usage
* 1432 NUnit hangs when reporting to TeamCity
* 1434 TestResult class needs to be thread-safe
* 1435 Parallel queue creation needs to be thread-safe
* 1436 CurrentFramework and Current Platform need to be more thread-safe
* 1439 EqualConstraint does Not use Equals Override on the Expected Object
* 1441 Add Linq for use internally in .NET 2.0 code
* 1446 TestOrderAttributeTests is not public
* 1450 SilverLight detection doesn't work when building on 32-bit OS
* 1457 Set the 2.0 build to ignore missing xml documentation
* 1463 Should TestResult.AssertCount have a public setter?
* 1464 TNode.EscapeInvalidXmlCharacters recreates Regex continually
* 1470 Make EventQueue and associated classes lock-less and thread safe
* 1476 Examine need for "synchronous" events in event queue
* 1481 TestCase with generic return type causes NullReferenceException
* 1483 Remoting exceptions during test execution
* 1484 Comparing Equality using `IEquatable<T>` Should Use Most Specific Method
* 1493 NUnit 2 test results report ParameterizedMethod but should be ParameterizedTest
* 1507 NullReferenceException when null arguments are used in TestFixtureAttribute
* 1513 Add new TeamCity extension to packages
* 1518 NUnit does not send the "testStarted" TeamCity service message when exception was thrown from SetUp/OneTimeSetUp
* 1520 Detect Portable, SilverLight and Compact and give error message
* 1528 Use of Sleep(0) in NUnit
* 1543 Blank name attribute in nunit2-formatted XML result file test-run element
* 1547 Create separate assembly for System.Linq compatibility classes
* 1548 Invalid Exception when engine is in a 32-bit process
* 1549 Changing default behavior for generating test case names
* 1551 Path in default .addins file for ConsoleRunner package may not exist
* 1555 EndsWith calls in Constraint constructor can cause major perf issues
* 1560 Engine writes setting file unnecessarily
* 1573 Move NUnit.Portable.Agent to new Repo
* 1579 NUnit v3 dangerously overrides `COMPLUS_Version` environment variable
* 1582 Mono 4.4.0 Causes Test Failures
* 1593 NUnit Console Runner 3.2.1 and Mono 4.4 throws RemotingException
* 1597 Move Portable agent to its own repository
* 1605 TeamCity package has no pre-release suffix
* 1607 nunit.nuget.addins discovery pattern is wrong then restored through project.json
* 1617 Load user profile on test runners

## NUnit 3.2.1 - April 19, 2016

### Framework

* The output and error files are now thread safe when running tests in parallel
* Added a .NET 3.5 build of the framework preventing conflicts with the compatibility classes in the 2.0 framework
* Added a SingleThreadedAttribute to be added to a TestFixture to indicate all child tests should run on the same thread

### Engine

* Unless required, run all tests within a fixture on the same thread
* Added an EventListener extension point
* Reduced memory usage

### Console Runner

* No longer probes for newer versions of the engine, instead uses the engine that is included with the console

### Issues Resolved

* 1413 Switch console to use a local engine
* 1410 Make OutFile and ErrFile stream writers synchronized
* 1406 TextCapture is not thread-safe but is used to intercept calls that are expected to be thread-safe
* 1405 ITestRunner.StopRun throws exception of type 'System.MissingMethodException'
* 1399 Fixed NullReference issue introduced by the fix for #681
* 1390 --testlist with file with blank first line causes IndexOutOfRangeException
* 1386 Bug when using Assert.Equals() with types that explicitly implement `IEquatable<T>`
* 1383 Skip SilverLight build if SDK not installed
* 1359 Compilation error in NUnitPortableDriverTests.cs
* 1352 Tests losing data setup on thread
* 1349 Collision on System.Func from nunit.framework with System.Core in .Net 3.5 (CS0433)
* 1338 BUILDING.txt is outdated
* 1333 Single Thread per Worker
* 1329 Unable to build without Compact Framework
* 1327 TestCaseSource in NUnit 3 converts an argument declared as String[] to String
* 1318 NUnit console runner fails with error code -100
* 1317 Getting CF framework unit tests running on CI build
* 1302 Create EventListener ExtensionPoint for the Engine
* 1266 SetCultureAttribute does not work if set on assembly level
* 1247 Potential memory issue
* 1231 Build may silently fail some tests
* 1208 Apartment on assembly level broken
* 1161 NUnit3-Console should disallow the combination of --inprocess and --x86, giving an error message
* 1141 Explicit Tests get run when using --where with some filters
* 773 Upgrade Travis CI from Legacy Infrastructure
* 640 Keep CF Build (and other future builds) in Sync
* 332 Add CF to the AppVeyor CI build

## NUnit 3.2 - March 5, 2016

### Framework

* Added an Order attribute that defines the order in which tests are run
* Added Assert.ThrowsAsync for testing if async methods throw an exception
* You can now compare unlike collections using Is.EquivalentTo().Using(...)
* Added the ability to add custom message formatters to MsgUtils
* TestCaseSourceAttribute now optionally takes an array of parameters that can be passed to the source method
* Added Is.Zero and Is.Not.Zero to the fluent syntax as a shorter option for Is.EqualTo(0) and Is.Not.EqualTo(0)

### Engine

* Engine extensions can be installed via NuGet packages

### Issues Resolved

* 170 Test Order Attribute
* 300 Create an NUnit Visual Studio Template
* 464 Async delegate assertions
* 532 Batch runner for SilverLight tests
* 533 Separate NUnitLite runner and auto-runner
* 681 NUnit agent cannot resolve test dependency assemblies when mixed mode initialization runs in the default AppDomain
* 793 Replace CoreEngine by use of Extensions
* 907 Console report tests are too fragile
* 922 Wrap Console in NUnitLite
* 930 Switch from MSBuild based build system to Cake
* 981 Define NUnit Versioning for post-3.0 Development
* 1004 Poor formatting of results for Assert.AreEqual(DateTimeOffset, DateTimeOffset)
* 1018 ArgumentException when 2.x version of NUnit Framework is in the bin directory
* 1022 Support Comparing Unlike Collections using Is.EquivalentTo().Using(...)
* 1044 Re-order Test Summary Errors/Failures
* 1066 ApartmentAttribute and TestCaseAttribute(s) do not work together
* 1103 Can't use TestCaseData from base class
* 1109 NullReferenceException when using inherited property for ValueSource
* 1113 Console runner and xml output consistency
* 1117 Fix misbehavior of Throws.Exception with non-void returning functions
* 1120 NUnitProject should parse .nunit project files containing Xml Declarations
* 1121 Usage of field set to null as value source leads to somewhat cryptic error
* 1122 Region may be disposed before test delegate is executed
* 1133 Provide a way to install extensions as nuget packages
* 1136 Don't allow V2 framework to update in V2 driver tests
* 1171 A bug when using Assert.That() with Is.Not.Empty
* 1185 Engine finds .NET 4.0 Client Profile twice
* 1187 ITestAssemblyRunner.StopRun as implemented by NUnitTestAssemblyRunner
* 1195 name attribute in test-suite and test-results element of output xml is different to nunit 2.6.4 using nunit2-format
* 1196 Custom value formatter for v3 via MsgUtils
* 1210 Available runtimes issues
* 1230 Add ability for `testcasedatasource` to have parameters passed to methods
* 1233 Add TestAssemblyRunner tests to both portable and SilverLight builds
* 1234 Have default NUnitLite Runner Program.cs return exit code
* 1236 Make AppVeyor NuGet feed more useable
* 1246 Introduce Is.Zero syntax to test for zero
* 1252 Exception thrown when any assembly is not found
* 1261 TypeHelper.GetDisplayName generates the wrong name for generic types with nested classes
* 1278 Fix optional parameters in TestCaseAttribute
* 1282 TestCase using Params Behaves Oddly
* 1283 Engine should expose available frameworks.
* 1286 value of the time attribute in nunit2 outputs depends on the machine culture
* 1297 NUnit.Engine nuget package improvements
* 1301 Assert.AreNotSame evaluates ToString unnecessarily

## NUnit 3.0.1 (3.0.5813) - December 1, 2015

### Console Runner

* The NUnit.Runners NuGet package was updated to become a meta-package that pulls in the NUnit.Console package
* Reinstated the --pause command line option that will display a message box allowing you to attach a debugger if the --debug option does not work

### Issues Resolved

* 994 Add max number of Agents to the NUnit project file
* 1014 Ensure NUnit API assembly updates with MSI installs
* 1024 Added --pause flag to console runner
* 1030 Update NUnit.Runners package to 3.0
* 1033 "No arguments were provided" with Theory and Values combination
* 1035 Check null arguments
* 1037 Async tests not working on Windows 10 Universal
* 1041 NUnit2XmlResult Writer is reporting Success when test fails
* 1042 NUnit2 reports on 3.0 is different than 2.6.4
* 1046 FloatingPointNumerics.AreAlmostEqualUlps throws OverflowException
* 1049 Cannot select Generic tests from command line
* 1050 Do not expose System.Runtime.CompilerServices.ExtensionAttribute to public
* 1054 Create nuget feeds for CI builds on AppVeyor
* 1055 nunit3 console runner --where option does not return error on invalid selection string
* 1060 Remove "Version 3" from NUnit Nuget Package
* 1061 Nunit30Settings.xml becomes corrupted
* 1062 Console.WriteLine statements in "OneTimeSetUp" and "OneTimeTearDown" annotated methods are not directed to the console when using nunit3-console.exe runner
* 1063 Error in Random Test

## NUnit 3.0.0 Final Release (3.0.5797) - November 15, 2015

### Issues Resolved

* 635 Mono 4.0 Support

## NUnit 3.0.0 Release Candidate 3 (3.0.5795) - November 13, 2015

### Engine

* The engine now only sets the config file for project.nunit to project.config if project.config exists. Otherwise, each assembly uses its own config, provided it is run in a separate AppDomain by itself.

> [!NOTE]
> It is not possible for multiple assemblies in the same AppDomain to use different configs. This is not an NUnit limitation, it's just how configs work!

### Issues Resolved

* 856 Extensions support for third party runners in NUnit 3.0
* 1003 Delete TeamCityEventHandler as it is not used
* 1015 Specifying .nunit project and --framework on command line causes crash
* 1017 Remove Assert.Multiple from framework

## NUnit 3.0.0 Release Candidate 2 (3.0.5790) - November 8, 2015

### Engine

* The IDriverFactory extensibility interface has been modified.

#### Issues Resolved

* 970  Define PARALLEL in CF build of NUnitLite
* 978  It should be possible to determine version of NUnit using nunit console tool
* 983  Inconsistent return codes depending on ProcessModel
* 986  Update docs for parallel execution
* 988  Don't run portable tests from NUnit Console
* 990  V2 driver is passing invalid filter elements to NUnit
* 991  Mono.Options should not be exposed to public directly
* 993  Give error message when a regex filter is used with NUnit V2
* 997  Add missing XML Documentation
* 1008 NUnitLite namespace not updated in the NuGet Packages

## NUnit 3.0.0 Release Candidate (3.0.5783) - November 1, 2015

### Framework

* The portable build now supports ASP.NET 5 and the new Core CLR.

> [!NOTE]
> The `nunit3-console` runner cannot run tests that reference the portable build. You may run such tests using NUnitLite or a platform-specific runner.

* `TestCaseAttribute` and `TestCaseData` now allow modifying the test name without replacing it entirely.
* The SilverLight packages for are now separate downloads.

### NUnitLite

* The NUnitLite runner now produces the same output display and XML results as the console runner.

### Engine

* The format of the XML result file has been finalized and documented.

### Console Runner

* The console runner program is now called `nunit3-console`.
* Console runner output has been modified so that the summary comes at the end, to reduce the need for scrolling.

### Issues Resolved

* 59 Length of generated test names should be limited
* 68 Customization of test case name generation
* 404 Split tests between SilverLight.runner and nunit.framework
* 575 Add support for ASP.NET 5 and the new Core CLR
* 783 Package separately for SilverLight
* 833 Intermittent failure of WorkItemQueueTests.StopQueue_WithWorkers
* 859 NUnit-Console output - move Test Run Summary to end
* 867 Remove Warnings from Ignored tests
* 868 Review skipped tests
* 887 Move environment and settings elements to the assembly suite in the result file
* 899 Colors for ColorConsole on grey background are too light
* 904 InternalPreserveStackTrace is not supported on all Portable platforms
* 914 Unclear error message from console runner when assembly has no tests
* 916 Console runner dies when test agent dies
* 918 Console runner --where parameter is case sensitive
* 920 Remove addins\nunit.engine.api.dll from NuGet package
* 929 Rename nunit-console.exe
* 931 Remove beta warnings from NuGet packages
* 936 Explicit skipped tests not displayed
* 939 Installer complains about .NET even if already installed
* 940 Confirm or modify list of packages for release
* 947 Breaking API change in ValueSourceAttribute
* 949 Update copyright in NUnit Console
* 954 NUnitLite XML output is not consistent with the engine's
* 955 NUnitLite does not display the where clause
* 959 Restore filter options for NUnitLite portable build
* 960 Intermittent failure of CategoryFilterTests
* 967 Run Settings Report is not being displayed.

## NUnit 3.0.0 Beta 5 (3.0.5767) - October 16, 2015

### Framework

* Parameterized test cases now support nullable arguments.
* The NUnit framework may now be built for the .NET Core framework. Note that this is only available through building the source code. A binary will be available in the next release.

### Engine

* The engine now runs multiple test assemblies in parallel by default
* The output XML now includes more information about the test run, including the text of the command used, any engine settings and the filter used to select tests.
* Extensions may now specify data in an identifying attribute, for use by the engine in deciding whether to load that extension.

### Console Runner

* The console now displays all settings used by the engine to run tests as well as the filter used to select tests.
* The console runner accepts a new option `--maxagents`. If multiple assemblies are run in separate processes, this value may be used to limit the number that are executed simultaneously in parallel.
* The console runner no longer accepts the --include and --exclude options. Instead, the new --where option provides a more general way to express which tests will be executed, such as --where "cat==Fast && Priority==High". See the docs for details of the syntax.
* The new --debug option causes NUnit to break in the debugger immediately before tests are run. This simplifies debugging, especially when the test is run in a separate process.

### Issues Resolved

* 41 Check for zeroes in Assert messages
* 254 Finalize XML format for test results
* 275 NUnitEqualityComparer fails to compare `IEquatable<T>` where second object is derived from `T`
* 304 Run test Assemblies in parallel
* 374 New syntax for selecting tests to be run
* 515 OSPlatform.IsMacOSX doesn't work
* 573 nunit-console hangs on Mac OS X after all tests have run
* 669 TeamCity service message should have assembly name as a part of test name.
* 689 The TeamCity service message "testFinished" should have an integer value in the "duration" attribute
* 713 Include command information in XML
* 719 We have no way to configure tests for several assemblies using NUnit project file and the common installation from msi file
* 735 Workers number in xml report file cannot be found
* 784 Build Portable Framework on Linux
* 790 Allow Extensions to provide data through an attribute
* 794 Make it easier to debug tests as well as NUnit itself
* 801 NUnit calls Dispose multiple times
* 814 Support nullable types with TestCase
* 818 Possible error in Merge Pull Request #797
* 821 Wrapped method results in loss of result information
* 822 Test for Debugger in NUnitTestAssemblyRunner probably should not be in CF build
* 824 Remove unused System.Reflection using statements
* 826 Randomizer uniqueness tests fail randomly!
* 828 Merge pull request #827 (issue 826)
* 830 Add ability to report test results synchronously to test runners
* 837 Enumerators not disposed when comparing IEnumerables
* 840 Add missing copyright notices
* 844 Pull Request #835 (Issue #814) does not build in CF
* 847 Add new --process:inprocess and --inprocess options
* 850 Test runner fails if test name contains invalid xml characters
* 851 Exclude' console option is not working in NUnit Lite
* 853 Cannot run NUnit Console from another directory
* 860 Use CDATA section for message, stack-trace and output elements of XML
* 863 Eliminate core engine
* 865 Intermittent failures of StopWatchTests
* 869 Tests that use directory separator char to determine platform misreport Linux on MaxOSX
* 870 NUnit Console Runtime Environment misreports on MacOSX
* 874 Add .NET Core Framework
* 878 Cannot exclude MacOSX or XBox platforms when running on CF
* 892 Fixed test runner returning early when executing more than one test run.
* 894 Give nunit.engine and nunit.engine.api assemblies strong names
* 896 NUnit 3.0 console runner not placing test result xml in --work directory

## NUnit 3.0.0 Beta 4 (3.0.5715) - August 25, 2015

### Framework

* A new RetryAttribute allows retrying of failing tests.
* New SupersetConstraint and Is.SupersetOf syntax complement SubsetConstraint.
* Tests skipped due to ExplicitAttribute are now reported as skipped.

### Engine

* We now use Cecil to examine assemblies prior to loading them.
* Extensions are no longer based on Mono.Addins but use our own extension framework.

#### Issues Resolved

* 125 3rd-party dependencies should be downloaded on demand
* 283 What should we do when a user extension does something bad?
* 585 RetryAttribute
* 642 Restructure MSBuild script
* 649 Change how we zip packages
* 654 ReflectionOnlyLoad and ReflectionOnlyLoadFrom
* 664 Invalid "id" attribute in the report for case "test started"
* 685 In the some cases when tests cannot be started NUnit returns exit code "0"
* 728 Missing Assert.That overload
* 741 Explicit Tests get run when using --exclude
* 746 Framework should send events for all tests
* 747 NUnit should apply attributes even if test is non-runnable
* 749 Review Use of Mono.Addins for Engine Extensibility
* 750 Include Explicit Tests in Test Results
* 753 Feature request: Is.SupersetOf() assertion constraint
* 755 TimeOut attribute doesn't work with TestCaseSource Attribute
* 757 Implement some way to wait for execution to complete in ITestEngineRunner
* 760 Packaging targets do not run on Linux
* 766 Added overloads for True()/False() accepting booleans
* 778 Build and build.cmd scripts invoke nuget.exe improperly
* 780 TeamCity fix
* 782 No sources for 2.6.4

## NUnit 3.0.0 Beta 3 (3.0.5674) - July 15, 2015

### Framework

* The RangeAttribute has been extended to support more data types including uint, long and ulong
* Added platform support for Windows 10 and fixed issues with Windows 8 and
   8.1 support
* Added async support to the portable version of NUnit Framework
* The named members of the TestCaseSource and ValueSource attributes must now be
   static.
* RandomAttribute has been extended to add support for new data types including uint, long, ulong, short, ushort, float, byte and sbyte
* TestContext.Random has also been extended to add support for new data types including uint, long, ulong, short, ushort, float, byte, sbyte and decimal
* Removed the dependency on Microsoft.Bcl.Async from the NUnit Framework assembly
   targeting .NET 4.0. If you want to write async tests in .NET 4.0, you will need
   to reference the NuGet package yourself.
* Added a new TestFixtureSource attribute which is the equivalent to TestCaseSource
   but provides for instantiation of fixtures.
* Significant improvements have been made in how NUnit deduces the type arguments of generic methods based on the arguments provided.

### Engine

* If the target framework is not specified, test assemblies that are compiled
   to target .NET 4.5 will no longer run in .NET 4.0 compatibility mode

### Console

* If the console is run without arguments, it will now display help

### Issues Resolved

* 47 Extensions to RangeAttribute
* 237 System.Uri .ctor works not properly under NUnit
* 244 NUnit should properly distinguish between .NET 4.0 and 4.5
* 310 Target framework not specified on the AppDomain when running against .Net 4.5
* 321 Rationalize how we count tests
* 472 Overflow exception and DivideByZero exception from the RangeAttribute
* 524 int and char do not compare correctly?
* 539 Truncation of string arguments
* 544 AsyncTestMethodTests for 4.5 Framework fails frequently on Travis CI
* 656 Unused parameter in Console.WriteLine found
* 670 Failing Tests in TeamCity Build
* 673 Ensure proper disposal of engine objects
* 674 Engine does not release test assemblies
* 679 Windows 10 Support
* 682 Add Async Support to Portable Framework
* 683 Make FrameworkController available in portable build
* 687 TestAgency does not launch agent process correctly if runtime type is not specified (i.e. v4.0)
* 692 PlatformAttribute_OperatingSystemBitNess fails when running in 32-bit process
* 693 Generic `Test<T>` Method cannot determine type arguments for fixture when passed as `IEnumerable<T>`
* 698 Require TestCaseSource and ValueSource named members to be static
* 703 TeamCity non-equal `flowid` for 'testStarted' and 'testFinished' messages
* 712 Extensions to RandomAttribute
* 715 Provide a data source attribute at TestFixture Level
* 718 RangeConstraint gives error with from and two args of differing types
* 723 Does nunit.nuspec require dependency on Microsoft.Bcl.Async?
* 724 Adds support for `Nullable<bool>` to Assert.IsTrue and Assert.IsFalse
* 734 Console without parameters doesn't show help

## NUnit 3.0.0 Beta 2 (3.0.5610) - May 12, 2015

### Framework

* The Compact Framework version of the framework is now packaged separately
   and will be distributed as a ZIP file and as a NuGet package.
* The NUnit 2.x RepeatAttribute was added back into the framework.
* Added Throws.ArgumentNullException
* Added GetString methods to NUnit.Framework.Internal.RandomGenerator to create repeatable random strings for testing
* When checking the equality of DateTimeOffset, you can now use the WithSameOffset modifier
* Some classes intended for internal usage that were public for testing
   have now been made internal. Additional classes will be made internal
   for the final 3.0 release.

### Engine

* Added a core engine which is a non-extensible, minimal engine for use by devices and similar situations where reduced functionality is compensated for by reduced size and simplicity of usage.

### Issues Resolved

* 22  Add OSArchitecture Attribute to Environment node in result xml
* 24  Assert on Dictionary Content
* 48  Explicit seems to conflict with Ignore
* 168  Create NUnit 3.0 documentation
* 196  Compare DateTimeOffsets including the offset in the comparison
* 217  New icon for the 3.0 release
* 316  NUnitLite TextUI Runner
* 320  No Tests found: Using parameterized Fixture and TestCaseSource
* 360  Better exception message when using non-BCL class in property
* 454  Rare registry configurations may cause NUnit to fail
* 478  RepeatAttribute
* 481  Testing multiple assemblies in NUnitLite
* 538  Potential bug using TestContext in constructors
* 546  Enable Parallel in NUnitLite/CF (or more) builds
* 551  TextRunner not passing the NumWorkers option to the ITestAssemblyRunner
* 556  Executed tests should always return a non-zero duration
* 559  Fix text of NuGet packages
* 560  Fix PackageVersion property on wix install projects
* 562  Program.cs in NUnitLite NuGet package is incorrect
* 564  NUnitLite Nuget package is Beta 1a, Framework is Beta 1
* 565  NUnitLite Nuget package adds Program.cs to a VB Project
* 568  Isolate packaging from building
* 570  ThrowsConstraint failure message should include stack trace of actual exception
* 576  Throws.ArgumentNullException would be nice
* 577  Documentation on some members of Throws falsely claims that they return `TargetInvocationException` constraints
* 579  No documentation for recommended usage of TestCaseSourceAttribute
* 580  TeamCity Service Message Uses Incorrect Test Name with NUnit2Driver
* 582  Test Ids Are Not Unique
* 583  TeamCity service messages to support parallel test execution
* 584  Non-runnable assembly has incorrect ResultState
* 609  Add support for integration with TeamCity
* 611  Remove unused --teamcity option from CF build of NUnitLite
* 612  MaxTime doesn't work when used for TestCase
* 621  Core Engine
* 622  nunit-console fails when use --output
* 628  Modify IService interface and simplify ServiceContext
* 631  Separate packaging for the compact framework
* 646  ConfigurationManager.AppSettings Params Return Null under Beta 1

## NUnit 3.0.0 Beta 1 (3.0.5562) - March 25, 2015

### General

* There is now a master windows installer for the framework, engine and console runner.

### Framework

* We no longer create a separate framework build for .NET 3.5. The 2.0 and 3.5 builds were essentially the same, so the former should now be used under both runtimes.
* A new Constraint, **DictionaryContainsKeyConstraint**, may be used to test that a specified key is present in a dictionary.
* **LevelOfParallelizationAttribute** has been renamed to **LevelOfParallelismAttribute**.
* The SilverLight runner now displays output in color and includes any text output created by the tests.
* The class and method names of each test are included in the output xml where applicable.
* String arguments used in test case names are now truncated to 40 rather than 20 characters.

### Engine

* The engine API has now been finalized. It permits specifying a minimum version of the engine that a runner is able to use. The best installed version of the engine will be loaded. Third-party runners may override the selection process by including a copy of the engine in their installation directory and specifying that it must be used.
* The V2 framework driver now uses the event listener and test listener passed to it by the runner. This corrects several outstanding issues  caused by events not being received and allows selecting V2 tests to  be run from the command-line, in the same way that V3 tests are selected.

### Console

* The console now defaults to not using shadowcopy. There is a new option **--shadowcopy** to turn it on if needed.

#### Issues Resolved

* 224 SilverLight Support
* 318 TestActionAttribute: Retrieving the TestFixture
* 428 Add ExpectedExceptionAttribute to C# samples
* 440 Automatic selection of Test Engine to use
* 450 Create master install that includes the framework, engine and console installs
* 477 Assert does not work with ArraySegment
* 482 nunit-console has multiple errors related to -framework option
* 483 Adds constraint for asserting that a dictionary contains a particular key
* 484 Missing file in NUnit.Console nuget package
* 485 Can't run v2 tests with nunit-console 3.0
* 487 NUnitLite can't load assemblies by their file name
* 488 Async setup and teardown still don't work
* 497 Framework installer should register the portable framework
* 504 Option --workers:0 is ignored
* 508 Travis builds with failure in engine tests show as successful
* 509 Under linux, not all mono profiles are listed as available
* 512 Drop the .NET 3.5 build
* 517 V2 FrameworkDriver does not make use of passed in TestEventListener
* 523 Provide an option to disable shadowcopy in NUnit v3
* 528 V2 FrameworkDriver does not make use of passed in TestFilter
* 530 Color display for SilverLight runner
* 531 Display text output from tests in SilverLight runner
* 534 Add `classname` and `methodname` to test result xml
* 541 Console help doesn't indicate defaults

## NUnit 3.0.0 Alpha 5 (3.0.5509) - January 30, 2015

### General

* A Windows installer is now included in the release packages.

### Framework

* TestCaseAttribute now allows arguments with default values to be omitted. Additionally, it accepts IncludePlatform and ExcludePlatform properties to specify the platforms on which the test case should be run.
* TestFixture and TestCase attributes now enforce the requirement that a reason needs to be provided when ignoring a test.
* SetUp, TearDown, OneTimeSetUp and OneTimeTearDown methods may now be async.
* String arguments over 20 characters in length are truncated when used as part of a test name.

### Engine

* The engine is now extensible using Mono.Addins. In this release, extension points are provided for FrameworkDrivers, ProjectLoaders and OutputWriters. The following addins are bundled as a part of NUnit:
  * A FrameworkDriver that allows running NUnit V2 tests under NUnit 3.0.
  * ProjectLoaders for NUnit and Visual Studio projects.
  * An OutputWriter that creates XML output in NUnit V2 format.
* DomainUsage now defaults to Multiple if not specified by the runner

### Console

* New options supported:
  * `--testlist` provides a list of tests to run in a file
  * `--stoponerror` indicates that the run should terminate when any test fails.

### Issues Resolved

* 20 TestCaseAttribute needs Platform property.
* 60 NUnit should support async setup, teardown, fixture setup and fixture teardown.
* 257  TestCaseAttribute should not require parameters with default values to be specified.
* 266  Pluggable framework drivers.
* 368  Create addin model.
* 369  Project loader addins
* 370  OutputWriter addins
* 403  Move ConsoleOptions.cs and Options.cs to Common and share...
* 419  Create Windows Installer for NUnit.
* 427  [TestFixture(Ignore=true)] should not be allowed.
* 437  Errors in tests under Linux due to hard-coded paths.
* 441  NUnit-Console should support --testlist option
* 442  Add `--stoponerror` option back to nunit-console.
* 456  Fix memory leak in RuntimeFramework.
* 459  Remove the Mixed Platforms build configuration.
* 468  Change default domain usage to multiple.
* 469  Truncate string arguments in test names in order to limit the length.

## NUnit 3.0.0 Alpha 4 (3.0.5476) - December 30, 2014

### Framework

* ApartmentAttribute has been added, replacing STAAttribute and MTAAttribute.
* Unnecessary overloads of Assert.That and Assume.That have been removed.
* Multiple SetUpFixtures may be specified in a single namespace.
* The Pairwise strategy test case generation algorithm has been improved.

### Engine

* A driver is now included, which allows running NUnit 2.x tests under NUnit 3.0.
* The engine can now load and run tests specified in a number of project formats:
  * NUnit (.nunit)
  * Visual Studio C# projects (.csproj)
  * Visual Studio F# projects (.vjsproj)
  * Visual Studio Visual Basic projects (.vbproj)
  * Visual Studio solutions (.sln)
  * Legacy C++ and Visual JScript projects (.csproj and .vjsproj) are also supported
  * Support for the current C++ format (.csxproj) is not yet available
* Creation of output files like TestResult.xml in various formats is now a
   service of the engine, available to any runner.

### Console

* The command-line may now include any number of assemblies and/or supported projects.

### Issues Resolved

* 37 Multiple SetUpFixtures should be permitted on same namespace
* 210 TestContext.WriteLine in an AppDomain causes an error
* 227 Add support for VS projects and solutions
* 231 Update C# samples to use NUnit 3.0
* 233 Update F# samples to use NUnit 3.0
* 234 Update C++ samples to use NUnit 3.0
* 265 Reorganize console reports for nunit-console and SilverLight
* 299 No full path to assembly in XML file under Compact Framework
* 301 Command-line length
* 363 Make Xml result output an engine service
* 377 CombiningStrategyAttributes don't work correctly on generic methods
* 388 Improvements to NUnitLite runner output
* 390 Specify exactly what happens when a test times out
* 396 ApartmentAttribute
* 397 CF SilverLight runner assembly has the wrong name
* 407 Assert.Pass() with ]]> in message crashes console runner
* 414 Simplify Assert overloads
* 416 NUnit 2.x Framework Driver
* 417 Complete work on NUnit projects
* 420 Create Settings file in proper location

## NUnit 3.0.0 Alpha 3 (3.0.5446) - November 29, 2014

### Breaking Changes

* NUnitLite tests must reference both the nunit.framework and SilverLight assemblies.

### Framework

* The NUnit and NUnitLite frameworks have now been merged. There is no longer any distinction
   between them in terms of features, although some features are not available on all platforms.
* The release includes two new framework builds: compact framework 3.5 and portable. The portable
   library is compatible with .NET 4.5, SilverLight 5.0, Windows 8, Windows Phone 8.1,
   Windows Phone SilverLight 8, Mono for Android and MonoTouch.
* A number of previously unsupported features are available for the Compact Framework:
  * Generic methods as tests
  * RegexConstraint
  * TimeoutAttribute
  * FileAssert, DirectoryAssert and file-related constraints

### Engine

* The logic of runtime selection has now changed so that each assembly runs by default
   in a separate process using the runtime for which it was built.
* On 64-bit systems, each test process is automatically created as 32-bit or 64-bit,
   depending on the platform specified for the test assembly.

### Console

* The console runner now runs tests in a separate process per assembly by default. They may
   still be run in process or in a single separate process by use of command-line options.
* The console runner now starts in the highest version of the .NET runtime available, making
   it simpler to debug tests by specifying that they should run in-process on the command-line.
* The -x86 command-line option is provided to force execution in a 32-bit process on a 64-bit system.
* A writability check is performed for each output result file before trying to run the tests.
* The -teamcity option is now supported.

### Issues Resolved

* 12   Compact framework should support generic methods
* 145  NUnit-console fails if test result message contains invalid xml characters
* 155  Create utility classes for platform-specific code
* 223  Common code for NUnitLite console runner and NUnit-Console
* 225  Compact Framework Support
* 238  Improvements to running 32 bit tests on a 64 bit system
* 261  Add portable NUnitLite build
* 284  NUnitLite Unification
* 293  CF does not have a CurrentDirectory
* 306  Assure NUnit can write result file
* 308  Early disposal of runners
* 309  NUnit-Console should support incremental output under TeamCity
* 325  Add RegexConstraint to compact framework build
* 326  Add TimeoutAttribute to compact framework build
* 327  Allow generic test methods in the compact framework
* 328  Use .NET Stopwatch class for compact framework builds
* 331  Alpha 2 CF does not build
* 333  Add parallel execution to desktop builds of NUnitLite
* 334  Include File-related constraints and syntax in NUnitLite builds
* 335  Re-introduce 'Classic' NUnit syntax in NUnitLite
* 336  Document use of separate obj directories per build in our projects
* 337  Update Standard Defines page for .NET 3.0
* 341  Move the NUnitLite runners to separate assemblies
* 367  Refactor XML Escaping Tests
* 372  CF Build TestAssemblyRunnerTests
* 373  Minor CF Test Fixes
* 378  Correct documentation for PairwiseAttribute
* 386  Console Output Improvements

### NUnit 3.0.0 Alpha 2 (3.0.5419) - November 2, 2014

### Breaking Changes

* The console runner no longer displays test results in the debugger.
* The NUnitLite compact framework 2.0 build has been removed.
* All addin support has been removed from the framework. Documentation of NUnit 3.0 extensibility features will be published in time for the beta release. In the interim, please ask for support on the nunit-discuss list.

### General

* A separate solution has been created for Linux
* We now have continuous integration builds under both Travis and AppVeyor
* The compact framework 3.5 build is now working and will be supported in future releases.

### New Features

* The console runner now automatically detects 32- versus 64-bit test assemblies.
* The NUnitLite report output has been standardized to match that of nunit-console.
* The NUnitLite command-line has been standardized to match that of nunit-console where they share the same options.
* Both nunit-console and NUnitLite now display output in color.
* ActionAttributes now allow specification of multiple targets on the attribute as designed. This didn't work in the first alpha.
* OneTimeSetUp and OneTimeTearDown failures are now shown on the test report. Individual test failures after OneTimeSetUp failure are no longer shown.
* The console runner refuses to run tests build with older versions of NUnit. A plugin will be available to run older tests in the future.

### Issues Resolved

* 222 Color console for NUnitLite
* 229 Timing failures in tests
* 241 Remove reference to Microsoft BCL packages
* 243 Create solution for Linux
* 245 Multiple targets on action attributes not implemented
* 246 C++ tests do not compile in VS2013
* 247 Eliminate trace display when running tests in debug
* 255 Add new result states for more precision in where failures occur
* 256 ContainsConstraint break when used with AndConstraint
* 264 Stacktrace displays too many entries
* 269 Add manifest to nunit-console and nunit-agent
* 270 OneTimeSetUp failure results in too much output
* 271 Invalid tests should be treated as errors
* 274 Command line options should be case insensitive
* 276 NUnit-console should not reference nunit.framework
* 278 New result states (ChildFailure and SetupFailure) break NUnit2XmlOutputWriter
* 282 Get tests for NUnit2XmlOutputWriter working
* 288 Set up AppVeyor CI build
* 290 Stack trace still displays too many items
* 315 NUnit 3.0 alpha: Cannot run in console on my assembly
* 319 CI builds are not treating test failures as failures of the build
* 322 Remove Stopwatch tests where they test the real .NET Stopwatch

## NUnit 3.0.0 Alpha 1 (3.0.5378) - September 22, 2014

### Breaking Changes

* Legacy suites are no longer supported
* Assert.NullOrEmpty is no longer supported (Use Is.Null.Or.Empty)

### General

* MsBuild is now used for the build rather than NAnt
* The framework test harness has been removed now that nunit-console is at a point where it can run the tests.

### New Features

* Action Attributes have been added with the same features as in NUnit 2.6.3.
* TestContext now has a method that allows writing to the XML output.
* TestContext.CurrentContext.Result now provides the error message and stack trace during teardown.
* Does prefix operator supplies several added constraints.

### Issues Resolved

* 6 Log4net not working with NUnit
* 13 Standardize command-line options for NUnitLite runner
* 17 No allowance is currently made for nullable arguments in TestCase parameter conversions
* 33 TestCaseSource cannot refer to a parameterized test fixture
* 54 Store message and stack trace in TestContext for use in TearDown
* 111 Implement Changes to File, Directory and Path Assertions
* 112 Implement Action Attributes
* 156 Accessing multiple AppDomains within unit tests result in SerializationException
* 163 Add --trace option to NUnitLite
* 167 Create interim documentation for the alpha release
* 169 Design and implement distribution of NUnit packages
* 171 Assert.That should work with any lambda returning bool
* 175 Test Harness should return an error if any tests fail
* 180 Errors in Linux CI build
* 181 Replace NAnt with MsBuild / XBuild
* 183 Standardize command-line options for test harness
* 188 No output from NUnitLite when selected test is not found
* 189 Add string operators to Does prefix
* 193 TestWorkerTests.BusyExecutedIdleEventsCalledInSequence fails occasionally
* 197 Deprecate or remove Assert.NullOrEmpty
* 202 Eliminate legacy suites
* 203 Combine framework, engine and console runner in a single solution and repository
* 209 Make Ignore attribute's reason mandatory
* 215 Running 32-bit tests on a 64-bit OS
* 219 Teardown failures are not reported

### Console Issues Resolved (Old nunit-console project, now combined with nunit)

* 2 Failure in TestFixtureSetUp is not reported correctly
* 5 CI Server for nunit-console
* 6 System.NullReferenceException on start nunit-console-x86
* 21 NUnitFrameworkDriverTests fail if not run from same directory
* 24 Debug' value for /trace option is deprecated in 2.6.3
* 38 Confusing Excluded categories output

## NUnit 2.9.7 - August 8, 2014

### Breaking Changes

* NUnit no longer supports void async test methods. You should use a Task return Type instead.
* The ExpectedExceptionAttribute is no longer supported. Use Assert.Throws() or Assert.That(..., Throws) instead for a more precise specification of where the exception is expected to be thrown.

### New Features

* Parallel test execution is supported down to the Fixture level. Use ParallelizableAttribute to indicate types that may be run in parallel.
* Async tests are supported for .NET 4.0 if the user has installed support for them.
* A new FileExistsConstraint has been added along with FileAssert.Exists and FileAssert.DoesNotExist
* ExpectedResult is now supported on simple (non-TestCase) tests.
* The Ignore attribute now takes a named parameter Until, which allows specifying a date after which the test is no longer ignored.
* The following new values are now recognized by PlatformAttribute: Win7, Win8, Win8.1, Win2012Server, Win2012ServerR2, NT6.1, NT6.2, 32-bit, 64-bit
* TimeoutAttribute is now supported under SilverLight
* ValuesAttribute may be used without any values on an enum or boolean argument. All possible values are used.
* You may now specify a tolerance using Within when testing equality of DateTimeOffset values.
* The XML output now includes a start and end time for each test.

### Issues Resolved

* 8    [SetUpFixture] is not working as expected
* 14   CI Server for NUnit Framework
* 21   Is.InRange Constraint Ambiguity
* 27   Values attribute support for enum types
* 29   Specifying a tolerance with "Within" doesn't work for DateTimeOffset data types
* 31   Report start and end time of test execution
* 36   Make RequiresThread, RequiresSTA, RequiresMTA inheritable
* 45   Need of `Enddate` together with Ignore
* 55   Incorrect XML comments for CollectionAssert.IsSubsetOf
* 62   Matches(Constraint) does not work as expected
* 63   Async support should handle Task return type without state machine
* 64   AsyncStateMachineAttribute should only be checked by name
* 65   Update NUnit site to show the new location of samples
* 66   Parallel Test Execution within test assemblies
* 67   Allow Expected Result on simple tests
* 70   EquivalentTo isn't compatible with IgnoreCase for dictionaries
* 75   Async tests should be supported for projects that target .NET 4.0
* 82   nunit-framework tests are timing out on Linux
* 83   Path-related tests fail on Linux
* 85   Culture-dependent NUnit tests fail on non-English machine
* 88   TestCaseSourceAttribute documentation
* 90   EquivalentTo isn't compatible with IgnoreCase for char
* 100  Changes to Tolerance definitions
* 110  Add new platforms to PlatformAttribute
* 113  Remove ExpectedException
* 118  Workarounds for missing InternalPreserveStackTrace in mono
* 121  Test harness does not honor the --worker option when set to zero
* 129  Standardize Timeout in the SilverLight build
* 130  Add FileAssert.Exists and FileAssert.DoesNotExist
* 132  Drop support for void async methods
* 153  Surprising behavior of DelayedConstraint pollingInterval
* 161  Update API to support stopping an ongoing test run

## NUnit 2.9.6 - October 4, 2013

### Main Features

* Separate projects for nunit-console and nunit.engine
* New builds for .NET 4.5 and SilverLight
* TestContext is now supported and includes an additional property, **Random**, which may be used to generate repeatable random values for use in a test.
* The external framework API is now stable; internal interfaces are separate from API
* Tests may be run in parallel on separate threads
* Solutions and projects now use VS2012 (except for Compact framework)

### Bug Fixes

* 463470 We should encapsulate references to pre-2.0 collections
* 498690 Assert.That() doesn't like properties with scoped setters
* 501784 Theory tests do not work correctly when using null parameters
* 531873 Feature: Extraction of unit tests from NUnit test assembly and calling appropriate one
* 611325 Allow Teardown to detect if last test failed
* 611938 Generic Test Instances disappear
* 655882 Make CategoryAttribute inherited
* 664081 Add Server2008 R2 and Windows 7 to PlatformAttribute
* 671432 Upgrade NAnt to Latest Release
* 676560 Assert.AreEqual does not support `IEquatable<T>`
* 691129 Add Category parameter to TestFixture
* 697069 Feature request: dynamic location for TestResult.xml
* 708173 NUnit's logic for comparing arrays - use `Comparer<T[]>` if it is provided
* 709062 "System.ArgumentException : Cannot compare" when the element is a list
* 712156 Tests cannot use AppDomain.SetPrincipalPolicy
* 719184 Platform dependency in src/ClientUtilities/util/Services/DomainManager.cs:40
* 719187 Using Path.GetTempPath() causes conflicts in shared temporary folders
* 735851 Add detection of 3.0, 3.5 and 4.0 frameworks to PlatformAttribute
* 736062 Deadlock when EventListener performs a Trace call + EventPump synchronization
* 756843 Failing assertion does not show non-linear tolerance mode
* 766749 net-2.0\nunit-console-x86.exe.config should have a `<startup />` element and also enable loadFromRemoteSources
* 770471 Assert.IsEmpty does not support IEnumerable
* 785460 Add Category parameter to TestCaseSourceAttribute
* 787106 EqualConstraint provides inadequate failure information for IEnumerables
* 792466 TestContext MethodName
* 794115 HashSet incorrectly reported
* 800089 Assert.Throws() hides details of inner AssertionException
* 848713 Feature request: Add switch for console to break on any test case error
* 878376 Add 'Exactly(n)' to the NUnit constraint syntax
* 882137 When no tests are run, higher level suites display as Inconclusive
* 882517 NUnit 2.5.10 doesn't recognize TestFixture if there are only TestCaseSource inside
* 885173 Tests are still executed after cancellation by user
* 885277 Exception when project calls for a runtime using only 2 digits
* 885604 Feature request: Explicit named parameter to TestCaseAttribute
* 890129 DelayedConstraint doesn't appear to poll properties of objects
* 892844 Not using Mono 4.0 profile under Windows
* 893919 DelayedConstraint fails polling properties on references which are initially null
* 896973 Console output lines are run together under Linux
* 897289 Is.Empty constraint has unclear failure message
* 898192 Feature Request: Is.Negative, Is.Positive
* 898256 `IEnumerable<T>` for Datapoints doesn't work
* 899178 Wrong failure message for parameterized tests that expect exceptions
* 904841 After exiting for timeout the teardown method is not executed
* 908829 TestCase attribute does not play well with variadic test functions
* 910218 NUnit should add a trailing separator to the ApplicationBase
* 920472 CollectionAssert.IsNotEmpty must dispose Enumerator
* 922455 Add Support for Windows 8 and Windows 2012 Server to PlatformAttribute
* 928246 Use assembly.Location instead of assembly.CodeBase
* 958766 For development work under TeamCity, we need to support nunit2 formatted output under direct-runner
* 1000181 Parameterized TestFixture with System.Type as constructor arguments fails
* 1000213 Inconclusive message Not in report output
* 1023084 Add Enum support to RandomAttribute
* 1028188 Add Support for SilverLight
* 1029785 Test loaded from remote folder failed to run with exception System.IODirectory
* 1037144 Add MonoTouch support to PlatformAttribute
* 1041365 Add MaxOsX and Xbox support to platform attribute
* 1057981 C#5 async tests are not supported
* 1060631 Add .NET 4.5 build
* 1064014 Simple async tests should not return `Task<T>`
* 1071164 Support async methods in usage scenarios of Throws constraints
* 1071343 Runner.Load fails on CF if the test assembly contains a generic method
* 1071861 Error in Path Constraints
* 1072379 Report test execution time at a higher resolution
* 1074568 Assert/Assume should support an async method for the ActualValueDelegate
* 1082330 Better Exception if SetCulture attribute is applied multiple times
* 1111834 Expose Random Object as part of the test context
* 1111838 Include Random Seed in Test Report
* 1172979 Add Category Support to NUnitLite Runner
* 1203361 Randomizer uniqueness tests sometimes fail
* 1221712 When non-existing test method is specified in -test, result is still "Tests run: 1, Passed: 1"
* 1223294 System.NullReferenceException thrown when ExpectedExceptionAttribute is used in a static class
* 1225542 Standardize command-line options for test harness

## NUnit 2.9.5 - July 30, 2010

### Bug Fixes

* 483836 Allow non-public test fixtures consistently
* 487878 Tests in generic class without proper TestFixture attribute should be invalid
* 498656 TestCase should show array values in GUI
* 513989 Is.Empty should work for directories
* 519912 Thread.CurrentPrincipal Set In TestFixtureSetUp Not Maintained Between Tests
* 532488 constraints from ConstraintExpression/ConstraintBuilder are not reusable
* 590717 categories contains dash or trail spaces is not selectable
* 590970 static TestFixtureSetUp/TestFixtureTearDown methods in base classes are not run
* 595683 NUnit console runner fails to load assemblies
* 600627 Assertion message formatted poorly by PropertyConstraint
* 601108 Duplicate test using abstract test fixtures
* 601645 Parameterized test should try to convert data type from source to parameter
* 605432 ToString not working properly for some properties
* 606548 Deprecate Directory Assert in 2.5 and remove it in 3.0
* 608875 NUnit Equality Comparer incorrectly defines equality for Dictionary objects

## NUnit 2.9.4 - May 4, 2010

### Bug Fixes

* 419411 Fixture With No Tests Shows as Non-Runnable
* 459219 Changes to thread principal cause failures under .NET 4.0
* 459224 Culture test failure under .NET 4.0
* 462019 Line endings needs to be better controlled in source
* 462418 Assume.That() fails if I specify a message
* 483845 TestCase expected return value cannot be null
* 488002 Should not report tests in abstract class as invalid
* 490679 Category in TestCaseData clashes with Category on ParameterizedMethodSuite
* 501352 VS2010 projects have not been updated for new directory structure
* 504018 Automatic Values For Theory Test Parameters Not Provided For bool And enum
* 505899 'Description' parameter in both TestAttribute and TestCaseAttribute is not allowed
* 523335 TestFixtureTearDown in static class not executed
* 556971 Datapoint(s)Attribute should work on `IEnumerable<T>` as well as on Arrays
* 561436 SetCulture broken with 2.5.4
* 563532 DatapointsAttribute should be allowed on properties and methods

## NUnit 2.9.3 - October 26, 2009

### Main Features

* Created new API for controlling framework
* New builds for .Net 3.5 and 4.0, compact framework 3.5
* Support for old style tests has been removed
* New ad-hoc runner for testing the framework

### Bug Fixes

* 432805 Some Framework Tests don't run on Linux
* 440109 Full Framework does not support "Contains"

## NUnit 2.9.2 - September 19, 2009

### Main Features

* NUnitLite code is now merged with NUnit
* Added NUnitLite runner to the framework code
* Added Compact framework builds

### Bug Fixes

* 430100 `Assert.Catch<T>` should return `T`
* 432566 NUnitLite shows empty string as argument
* 432573 Mono test should be at runtime

## NUnit 2.9.1 - August 27, 2009

### Main Features

* Created a separate project for the framework and framework tests
* Changed license to MIT / X11
* Created Windows installer for the framework

### Bug Fixes

* 400502 NUnitEqualityComparer.StreamsE­qual fails for same stream
* 400508 TestCaseSource attribute is not working when Type is given
* 400510 TestCaseData variable length ctor drops values
* 417557 Add SetUICultureAttribute from NUnit 2.5.2
* 417559 Add Ignore to TestFixture, TestCase and TestCaseData
* 417560 Merge Assert.Throws and Assert.Catch changes from NUnit 2.5.2
* 417564 TimeoutAttribute on Assembly

## Earlier Releases

* Release Notes for [NUnit 2.6 through 2.6.4](https://www.nunit.org/?p=releaseNotes&r=2.6.4)
* Release Notes for [NUnit 2.5 through 2.5.10](https://www.nunit.org/?p=releaseNotes&r=2.5.10)
* Release Notes for [NUnit 2.4 through 2.4.8](https://www.nunit.org/?p=releaseNotes&r=2.4.8)
* Release Notes for [NUnit 2.0 through 2.2.10](https://www.nunit.org/?p=releaseNotes&r=2.2.10)
