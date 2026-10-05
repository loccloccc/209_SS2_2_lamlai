# Bài 2: Tạo User thường và cấu hình Sudo

## 1. Tạo user `devops`

```bash
adduser devops
usermod -aG sudo devops
groups devops
```

Kết quả:

```text
devops : devops sudo users
```

## 2. Cấu hình SSH Key

Sao chép thư mục SSH:

```bash
rsync --archive --chown=devops:devops /root/.ssh /home/devops/
```

Thêm public key từ máy Windows vào:

```text
/home/devops/.ssh/authorized_keys
```

Thiết lập quyền:

```bash
chown -R devops:devops /home/devops/.ssh
chmod 700 /home/devops/.ssh
chmod 600 /home/devops/.ssh/authorized_keys
```

## 3. Kiểm tra SSH

Từ máy Windows:

```cmd
ssh -i C:\Users\loc\.ssh\id_rsa devops@221.121.1.170
```

Kiểm tra:

```bash
whoami
```

Kết quả:

```text
devops
```

## 4. Kiểm tra quyền quản trị

```bash
sudo whoami
```

Kết quả:

```text
root
```

## 5. Kết quả

- Tạo user `devops`: Thành công
- Thêm `devops` vào nhóm `sudo`: Thành công
- Cấu hình SSH Key: Thành công
- SSH bằng `devops`: Thành công
- `sudo whoami`: trả về `root`


