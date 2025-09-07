---
{"dg-publish":true,"dg-path":"Tutorial/Tạo Github Pages dựa trên template.md","permalink":"/tutorial/tao-github-pages-dua-tren-template/","title":"Tạo Github Pages dựa trên template Just the Docs","tags":["tutorial"],"created":"2025-09-07T23:28:44.831+07:00"}
---


# Result
- https://tutran21195.github.io/steg-labs/
- Cấu trúc thư mục của site: https://github.com/TuTran21195/steg-labs/tree/gh-pages

# Tách biệt 2 nhánh (nhánh `main` & `gh-pages` )

- Nhánh `main` → Lưu các thành phần trong dự án gốc.
- Nhánh `gh-pages` → chứa thêm template Just the Docs, chuyên để edit tài liệu doc cho trang `.github.io/repo-name/`

# Installation
- Clone dự án của mình về local để dễ push lên remote.
- Ở một nơi nào đó, clone dự án sau về: [TuTran21195/just-the-docs: Using Github Pages Template](https://github.com/TuTran21195/just-the-docs/)
- Copy tất cả các file trong repo mẫu đó (trừ `.git` nhé) vào trong nhánh `gh-page` của mình, cứ để thẳng ở thư mục gốc ấy.
- Chỉnh sửa file `_config.yml` với các thành phần như sau:

```yml
title: Audio Steganography
description: A collection of labs for learning audio steganography techniques.
theme: just-the-docs

url: https://tutran21195.github.io/steg-labs/ # sửa thành link github.io của mình

aux_links: # cái này là link hiển thị ở góc phải bên trên (cạnh thanh search của site github.io). Xóa hẳn nó đi nếu ko cần đến.
  Labs Repository: https://github.com/TuTran21195/steg-labs
aux_links_new_tab: true

```

- Chỉnh sửa các file trong `.github/workflow`:
```yml
# ci.yml
name: CI
on:
  push:
    branches: ["gh-pages"] # chỉnh sửa cái này thành nhánh mà chứa template Just the Doc để nó build khi có gì đó push lên nhánh này. Theo hướng dẫn này thì để nguyên là "gh-pages" là oke.
  pull_request:
```

```yml
# pages.yml
# This workflow uses actions that are not certified by GitHub.

# They are provided by a third-party and are governed by

# separate terms of service, privacy policy, and support

# documentation.

  

# Sample workflow for building and deploying a Jekyll site to GitHub Pages

name: Deploy Jekyll site to Pages

on:
  push:
    branches: ["gh-pages"] # chỉnh sửa cái này thành nhánh mà chứa template Just the Doc để nó build khi có gì đó push lên nhánh này. Theo hướng dẫn này thì để nguyên là "gh-pages" là oke.

  # Allows you to run this workflow manually from the Actions tab

  workflow_dispatch:
```

- Sửa con bot `dependabot` cho rõ ràng hơn:
```yml
version: 2
updates:
  - package-ecosystem: bundler
    directory: /
    schedule:
      interval: daily
    allow:
      - dependency-type: direct
    target-branch: gh-pages # Thêm dòng này để Dependabot tạo Pull Request cho nhánh gh-pages
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: daily
      time: "10:00"
    open-pull-requests-limit: 10
    target-branch: gh-pages # Thêm dòng này để Dependabot tạo Pull Request cho nhánh gh-pages
```

- Sau đó: go to `Settings > Pages > Build and deployment > Source`, and select `GitHub Actions`

- Vào tab `Action` để xem quá trình nó build & deploy xem có lỗi gì không thì check log ở đó.

# Ultilized
- Các tài liệu thì tạo một folder là `/docs` để lưu các note mình muốn hiển thị.
- Xem mẫu cấu trúc thư mục và cấu trúc file doc của dự án sau: [TuTran21195/steg-labs at branch gh-pages](https://github.com/TuTran21195/steg-labs/tree/gh-pages)
### Navigation
#### Thêm trang đơn lẻ vào thanh điều hướng

- Trong tệp Markdown (ví dụ: docs/new-page.md), thêm hoặc chỉnh sửa nav_order trong front matter:
    
    ```markdown
    ---
    title: Trang Mới
    layout: default
    nav_order: 3  # Thứ tự xuất hiện trong thanh điều hướng
    ---
    ```
    
    - nav_order: Quy định thứ tự hiển thị (số nhỏ xuất hiện trước). Ví dụ, nav_order: 1 sẽ đặt trang ở đầu.
    - Nếu không có nav_order, trang sẽ không xuất hiện trong thanh điều hướng trừ khi được cấu hình trong _config.yml.

#### Tạo nhóm (menu con) trong thanh điều hướng

Nếu bạn muốn nhóm các trang thành một mục menu con (parent-child hierarchy), hãy thêm parent vào front matter:

> [!key-point] Note
> Các trang con không nhất thiết phải set giá trị cho `nav_order`, nó sẽ tự sắp xếp theo alpabet của title của các trang con đó.
> Các trang lẻ, trang cha,... thì nên set giá trị `nav_order` một cách tường minh và tránh trùng nhau để không gây ra lỗi.

1. Tạo một trang cha (parent) nếu cần:
    
    
    
    ```markdown
    # docs/parent-page.md
    ---
    title: Hướng Dẫn
    layout: default
    nav_order: 2
    has_children: true  # Bật menu con
    ---
    ```
    
2. Tạo các trang con:
    
    
    
    ```markdown
    # docs/child-page1.md
    ---
    title: Hướng Dẫn 1
    layout: default
    parent: Hướng Dẫn  # Liên kết với trang cha bằng title của trang cha
    nav_order: 1
    ---
    
    Nội dung hướng dẫn 1.
    ```
    
    
    
    ```markdown
    # docs/child-page2.md
    ---
    title: Hướng Dẫn 2
    layout: default
    parent: Hướng Dẫn # Liên kết với trang cha bằng title của trang cha
    nav_order: 2 
    ---
    
    Nội dung hướng dẫn 2.
    ```
    
    - **Kết quả**: Thanh điều hướng sẽ hiển thị mục “Hướng Dẫn” với hai trang con “Hướng Dẫn 1” và “Hướng Dẫn 2”.

### TOC
- với các trang cha thì nó sẽ tự xuất hiện TOC là các trang con.
- Để tạo TOC các heading trong một trang đơn: [In-Page Navigation | Just the Docs](https://just-the-docs.com/docs/navigation/in-page/)
For an _ordered_ table of contents, use the following markdown code:

``` markdown
1. TOC
{:toc}
```

The `{:toc}` line _must_ follow the `1. TOC` line, which begins a list.

For an _unordered_ table of contents, instead use the following markdown code:

``` markdown
- TOC
{:toc}
```

### Callout
- [Callouts | Just the Docs](https://just-the-docs.com/docs/ui-components/callouts/)
Trước tiên phải vào file `_config.yml` và định nghĩa các callout mà mình mong muốn:
```yml
callouts_level: quiet # or loud
callouts:
  highlight:
    color: yellow
  important:
    title: Important # nếu để thêm trường title thì title của nó sẽ luôn là chữ này
    color: blue
  new:
    title: New
    color: green
  note:
    title: Note
    color: purple
  warning:
    title: Warning
    color: red
  tip:
    title: Tips
    color: green
  info:
    title: Info
    color: blue
```

- Muốn dùng callout trong page thì:
```markdown
{: .highlight }
> A paragraph in callout.....
> 
> ...
```

# Related
- Ngoài theme này ra thì có thể xem thêm các theme github pages khác tại [Free Jekyll Themes](https://jekyllthemes.io/free)