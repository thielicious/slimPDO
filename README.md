# slimPDO
##### Tweaked extension for prepared statements and queries
---

<br>

## INTRODUCTION

Just a small tweaked PDO extension for my own personal use.

<br>

## SETUP INFORMATION

Use your CLI and enter the following to clone:<br>
`git clone https://github.com/thielicious/slimPDO.git`

<br>

## USAGE

Since it's packed in a trait called **DB**, you only need to `use` it in any class you want:
```
if (trait_exists("DB")) { // optional
  class some_class {
    use DB;
    // ...
```
Now, instead of:
```
$stmt = $this->pdo->prepare($sql);
$stmt->execute([":param" => $value]);
```
Just do this:
```
$this->pdo->prep($sql,[":param" => $value]);
```
Example:
```
foreach ($this->pdo->prep(
	"SELECT * FROM `members` WHERE `usr_name` = :name",
	[":name" => $username]
	) as $user) {
	return $user->usr_id;
}
```
This extension can be used as a callback hence very useful in loops. No separate declaration needed.

<br>
<br>

###### Feel free to pull/edit/fork w/e.

---
**[thielicious.github.io](http://thielicious.github.io)**
