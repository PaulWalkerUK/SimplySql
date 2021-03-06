# SimplySql

## Introduction

[![Powershell Gallery](https://img.shields.io/powershellgallery/v/SimplySql.svg)](https://www.powershellgallery.com/packages/SimplySql/)

Querying SQL (SQL Server, Oracle, PostgreSql, SQLite, & mySql) the PowerShell way: simple commands... powerful opportunities.

SimplySql is a module that provides an intuitive set of cmdlets for talking to databases that abstracts the vendor specifics, allowing you to focus on getting work done.

The basic pattern is to connect to a database, invoke one or more sql statements and then close your database connection. This module provides cmdlets that map to this basic pattern.  Each Provider has its own 'Open-*Connection' cmdlet, but the remaining cmdlets are provider agnostic (MSSQL: Open-SqlConnection, Oracle: Open-OracleConnection, SQLite: Open-SQLiteConnection, etc).  You can have multiple connections open, just distinguish them through the use of the -ConnectionName parameter on every command (if no ConnectionName is specified, it defaults to 'default').

    Open-*Connection -DataSource "SomeServer" -InitialCatalog "SomeDB"
    $data = Invoke-SqlQuery -query "SELECT * FROM someTable"
    Close-SqlConnection

See the [Wiki](https://github.com/mithrandyr/SimplySql/wiki) for more details

## Status

Version 1.3.x is in the repository, supports SQL Server, SQLite, MySql, Oracle and PostGreSql.  Please note that this project is actively in development and should be considered beta, though perfectly usuable.

It has been released to PowerShellGallery.  Installation is as simple as

    Install-Module SimplySql -Scope CurrentUser

This module requires PowerShell Version 5.0 or greater

## Latest Version

### 1.5.4

* Fixed issue with loading the Geometry npgsql extension (Npgsql.NetTopologySuite) when database in connection string did not have PostGIS installed.
* Automatically load geometry npgsql extension on database switch and on re-opening the connection (if current database has PostGIS installed).

### 1.5.3

* Fixed issue with Geometry not being supported in PostGre provider.

### 1.5.2

* Fixed issue with OracleProvider -- binding by position rather than by parameter name. (@Abrechnung1)

### 1.5.1

* Updated tests for Pester v4
* Fixed issue with transactions for MSSQL.
* Fixed issue with ```Show-SqlConnection -all | Close-SqlConnection``` when there are no open connections.
* Updated MySql Provider to 8.0.12, added parameter for SSLmode
* Updated SQLite provider to 1.0.109.1
* Updated Oracle provider to 18.3 (added support for oracleCredential)
* Updated PostGre provider (npgsql) to 4.0.2

[View Version History](VersionHistory.md)