# 网站部署指南

## 域名配置

您的域名是：`www.nextutorai.com`

## 部署选项

### 1. 静态网站托管服务（推荐）

#### GitHub Pages
1. 将代码上传到GitHub仓库
2. 在仓库设置中启用GitHub Pages
3. 设置自定义域名：`www.nextutorai.com`
4. 添加CNAME文件指向您的域名

#### Netlify
1. 注册Netlify账户
2. 连接GitHub仓库或直接上传文件
3. 设置自定义域名：`www.nextutorai.com`
4. 配置DNS记录

#### Vercel
1. 注册Vercel账户
2. 导入GitHub仓库
3. 设置自定义域名：`www.nextutorai.com`
4. 自动部署

### 2. 传统虚拟主机

1. 购买支持Apache的虚拟主机服务
2. 上传所有文件到网站根目录
3. 确保 `.htaccess` 文件生效
4. 配置域名DNS记录

### 3. VPS/云服务器

1. 安装Apache或Nginx
2. 配置虚拟主机
3. 上传文件到网站目录
4. 配置SSL证书

## DNS配置

在您的域名管理面板中，添加以下DNS记录：

```
类型: A
名称: @
值: [您的服务器IP地址]

类型: A
名称: www
值: [您的服务器IP地址]

类型: CNAME
名称: www
值: [如果使用CDN，填写CDN地址]
```

## SSL证书配置

### Let's Encrypt（免费）
```bash
# 安装Certbot
sudo apt-get install certbot python3-certbot-apache

# 获取SSL证书
sudo certbot --apache -d nextutorai.com -d www.nextutorai.com
```

### 商业SSL证书
1. 购买SSL证书
2. 在服务器上安装证书
3. 配置Apache/Nginx使用HTTPS

## 性能优化

### 1. CDN配置
推荐使用Cloudflare：
1. 注册Cloudflare账户
2. 添加域名：`nextutorai.com`
3. 更新DNS记录
4. 启用HTTPS和缓存

### 2. 图片优化
- 使用WebP格式图片
- 压缩图片文件大小
- 使用响应式图片

### 3. 缓存配置
已在 `.htaccess` 文件中配置了缓存规则

## 监控和维护

### 1. 网站监控
- 设置Uptime监控
- 配置错误日志监控
- 设置性能监控

### 2. 定期维护
- 更新SSL证书
- 检查安全更新
- 备份网站文件
- 监控网站性能

## 安全配置

### 1. 安全头设置
已在 `.htaccess` 文件中配置了安全头

### 2. 防火墙配置
```bash
# 只允许必要端口
sudo ufw allow 80
sudo ufw allow 443
sudo ufw allow 22
sudo ufw enable
```

### 3. 定期安全扫描
- 使用安全扫描工具
- 检查漏洞更新
- 监控异常访问

## 备份策略

### 1. 文件备份
```bash
# 创建备份脚本
#!/bin/bash
tar -czf backup-$(date +%Y%m%d).tar.gz /var/www/html/
```

### 2. 数据库备份（如果有）
```bash
# MySQL备份
mysqldump -u username -p database_name > backup.sql
```

## 故障排除

### 常见问题

1. **网站无法访问**
   - 检查DNS配置
   - 检查服务器状态
   - 检查防火墙设置

2. **HTTPS不工作**
   - 检查SSL证书
   - 检查Apache/Nginx配置
   - 检查端口443是否开放

3. **页面加载慢**
   - 启用CDN
   - 优化图片
   - 检查服务器性能

## 联系信息

如有部署问题，请联系：
- 邮箱：nextutor@nextutorai.com
- 电话：+86 13328031168

---

**注意**：部署前请确保所有文件都已正确配置，特别是域名相关的设置。 