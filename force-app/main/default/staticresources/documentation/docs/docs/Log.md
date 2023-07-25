---
layout: default
---
# Log

Generic logging framework that persists across DML reversions
by publishing a Platform Event


**Group** Shared Code

## Constructors
### `private Log()`

establishes the buffer, if one doesn't yet exist private, to ensure we can't directly construct this class. Use the Singleton, Luke.

---
## Fields

### `private buffer` → `List<LogMessage>`


private list of LogMessage objects to be published in the future

### `private currentInstance` → `Log`


private instance of this log class that backs the singleton get() method.

---
## Methods
### `public static get()`

Singleton pattern `get` method.

#### Returns

|Type|Description|
|---|---|
|Log|`Log`|

### `public add(String messageToLog)`

Add a message to the buffer without publishing it. Assumes a null severity

#### Parameters

|Param|Description|
|---|---|
|`messageToLog`|The string message to add to the buffer.|

### `public add(String messageToLog, LogSeverity severity)`

Add a message to the buffer without publishing it.

#### Parameters

|Param|Description|
|---|---|
|`messageToLog`|The string message to add to the buffer.|
|`severity`|LogSeverity enum|

### `public add(Exception exceptionToLog)`

Add an formated exception message to the buffer without publishing it. Assumes a null Severity

#### Parameters

|Param|Description|
|---|---|
|`exceptionToLog`|Exception to format and log|

### `public add(Exception exceptionToLog, LogSeverity severity)`

Add an formated exception message to the buffer without publishing it.

#### Parameters

|Param|Description|
|---|---|
|`exceptionToLog`|Exception to format and log|
|`severity`|LogSeverity enum|

### `public publish()`

Publish any messages currently in the buffer, without adding any new ones.

### `public publish(Exception exceptionToLog)`

Auto-format exception details, add it to the log buffer, and then publish the current buffer. Use the equivelent add method if you intend to add multiple messages rapidly to minimize DML usage.

#### Parameters

|Param|Description|
|---|---|
|`exceptionToLog`|exception to format and log|

### `public publish(String messageToLog)`

Auto-format a custom log message string, add it to the log buffer, and then publish the current buffer. Use the equivelent add method if you intend to add multiple messages rapidly to minimize DML usage.

#### Parameters

|Param|Description|
|---|---|
|`messageToLog`|String to log|

---
