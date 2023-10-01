# 02-git-04-tools
Домашнее задание к занятию «Инструменты Git»
1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea. 

git log aefea
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Thu Jun 18 10:29:58 2020 -0400

    Update CHANGELOG.md

2. Какому тегу соответствует коммит 85024d3? - 

git log 85024d3
commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)

3. Сколько родителей у коммита b8d720? Напишите их хеши.-

git show -s --format=%p b8d720
56cd7859e0 9ea88f22fc

git log b8d720
commit b8d720f8340221f2146e4e4870bf2ee0bc48f2d5
Merge: 56cd7859e0 9ea88f22fc

4. Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.

git log --pretty=oneline v0.12.23...v0.12.24
33ff1c03bb960b332be3af2e333462dde88b279e (tag: v0.12.24) v0.12.24
b14b74c4939dcab573326f4e3ee2a62e23e12f89 [Website] vmc provider links
3f235065b9347a758efadc92295b540ee0a5e26e Update CHANGELOG.md
6ae64e247b332925b872447e9ce869657281c2bf registry: Fix panic when server is unreachable
5c619ca1baf2e21a155fcdb4c264cc9e24a2a353 website: Remove links to the getting started guide's old location       
06275647e2b53d97d4f0a19a0fec11f6d69820b5 Update CHANGELOG.md
d5f9411f5108260320064349b757f55c09bc4b80 command: Fix bug when using terraform login on Windows
4b6d06cc5dcb78af637bbb19c198faff37a066ed Update CHANGELOG.md
dd01a35078f040ca984cdd349f18d0b67e486c35 Update CHANGELOG.md
225466bc3e5f35baa5d07197bbc079345b77525e Cleanup after v0.12.23 release

5. Найдите коммит, в котором была создана функция func providerSource, 
её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).

$ git log --reverse -p -S 'func providerSource' 

func providerSource(services *disco.Disco) getproviders.Source

git grep --break --heading  'func providerSource'
provider_source.go
func providerSource(configs []*cliconfig.ProviderInstallation, services *disco.Disco) (getproviders.Source, tfdiags.Diagnostics) {
func providerSourceForCLIConfigLocation(loc cliconfig.ProviderInstallationLocation, services *disco.Disco) (getproviders.Source, tfdiags.Diagnostics) {


6. Найдите все коммиты, в которых была изменена функция globalPluginDirs.

git log --oneline -S 'globalPluginDirs'
65c4ba7363 Remove terraform binary
125eb51dc4 Remove accidentally-committed binary
22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
7c7e5d8f0a Don't show data while input if sensitive
35a058fb3d main: configure credentials from the CLI config file
c0b1761096 prevent log output during init
8364383c35 Push plugin discovery down into command package

7. Кто автор функции synchronizedWriters

git log --reverse --pretty=format:"%an %ad" -S 'synchronizedWriters'
Martin Atkins Wed May 3 16:25:41 2017 -0700
James Bardin Wed Oct 21 13:06:23 2020 -0400
James Bardin Mon Nov 30 18:02:04 2020 -0500



