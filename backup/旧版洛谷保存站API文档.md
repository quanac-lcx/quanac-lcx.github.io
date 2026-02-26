![](https://w.saobby.com/w/pwcoaejf)

> [!CAUTION]
>
> AI生成。不过这玩意貌似也没啥用。喜欢的话关注主包吧

本文档列出了 `luogu-saver` 项目的所有API端点。项目基于Express.js构建，提供多种功能包括文章、剪贴板、用户信息保存、犇犇抓取、管理后台等。

## API 基础信息

- **基础URL**: `https://www.luogu.me` (根据配置可能不同)
- **响应格式**: JSON，使用统一响应格式 `{ success: boolean, data?: any, message?: string }`
- **认证**: 部分API需要登录（通过Token认证）

## API 端点分类

### 1. 公共API (`/api/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/api/statistic` | 获取站点统计信息 | 公开 |
| GET | `/api/ads` | 获取广告配置 | 公开 |
| POST | `/api/deletion/:type/:id` | 提交删除请求 | 需要登录 |

### 2. 用户认证 (`/user/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| POST | `/user/login` | 使用Token登录 | 公开 |
| POST | `/user/logout` | 退出登录 | 需要登录 |
| GET | `/user/save/:uid` | 请求保存用户主页 | 公开 |

### 3. Token管理 (`/token/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| POST | `/token/generate` | 生成新的Token | 公开 |

### 4. 文章相关 (`/article/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/article/save/:id` | 请求保存文章 | 公开 |
| GET | `/article/recent` | 获取最近文章列表（HTML） | 公开 |
| GET | `/article/rss` | 文章RSS订阅 | 公开 |
| GET | `/article/:id` | 查看文章详情（HTML） | 公开 |

### 5. 剪贴板相关 (`/paste/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/paste/save/:id` | 请求保存剪贴板 | 公开 |
| GET | `/paste/:id` | 查看剪贴板详情（HTML） | 公开 |

### 6. 任务管理 (`/task/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/task/query` | 查询任务状态 | 公开 |
| GET | `/task/:id` | 查看任务详情（HTML） | 公开 |

### 7. 犇犇相关 (`/benben/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/benben/api/statistic` | 获取犇犇统计信息 | 公开 |
| GET | `/benben/api/at/:username` | 查询被@的犇犇 | 公开 |
| POST | `/benben/api/search/advanced` | 高级搜索（未实现） | 公开 |
| GET | `/benben/api/search/feed/:uid` | 获取用户犇犇动态 | 公开 |
| GET | `/benben/save/:id` | 请求抓取用户犇犇 | 公开 |
| GET | `/benben/mentions` | 被@查询页面（HTML） | 公开 |
| GET | `/benben/history` | 用户历史页面（HTML） | 公开 |
| GET | `/benben/crawl` | 犇犇抓取页面（HTML） | 公开 |

### 8. 陶片放逐 (`/judgement/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/judgement/save` | 请求保存陶片放逐列表 | 公开 |
| GET | `/judgement/` | 查看陶片放逐列表（HTML） | 公开 |

### 9. 通知系统 (`/notification/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/notification/api` | 获取用户通知 | 需要登录 |
| POST | `/notification/:id/read` | 标记通知为已读 | 需要登录 |
| POST | `/notification/read-all` | 标记所有通知为已读 | 需要登录 |
| GET | `/notification/` | 通知页面（HTML） | 需要登录 |

### 10. 冬日绘板 (`/paintboard/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| POST | `/paintboard/apply` | 申请绘板Token | 需要登录 |
| POST | `/paintboard/refresh` | 刷新绘板Token | 需要登录 |
| GET | `/paintboard/verify/:key` | 验证访问密钥 | 公开 |
| GET | `/paintboard/` | 绘板查看页面（HTML） | 公开 |
| GET | `/paintboard/webgl` | WebGL绘板页面（HTML） | 公开 |
| GET | `/paintboard/token` | Token申请页面（HTML） | 需要登录 |

### 11. 题目相关 (`/problem/*`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/problem/` | 题目列表页面（HTML） | 公开 |

### 12. 管理后台 (`/admin/*`)

所有管理API都需要管理员权限。

#### 12.1 作业管理
| 方法 | 路径 | 描述 |
|------|------|------|
| POST | `/admin/api/jobs/cleanup` | 执行清理作业 |
| POST | `/admin/api/jobs/update-problems` | 执行更新题目作业 |

#### 12.2 内容管理
| 方法 | 路径 | 描述 |
|------|------|------|
| POST | `/admin/api/restore/:type/:id` | 恢复已删除项目 |
| DELETE | `/admin/api/delete/:type/:id` | 删除项目 |
| POST | `/admin/api/mark-deleted/:type/:id` | 标记项目为已删除 |

#### 12.3 Token管理
| 方法 | 路径 | 描述 |
|------|------|------|
| DELETE | `/admin/api/tokens/:id` | 删除Token |
| POST | `/admin/api/tokens/:id/role` | 更新Token角色 |

#### 12.4 系统管理
| 方法 | 路径 | 描述 |
|------|------|------|
| GET | `/admin/api/queue/status` | 获取队列状态 |
| GET | `/admin/api/accounts` | 获取账户配置 |
| POST | `/admin/api/accounts` | 更新账户配置 |
| POST | `/admin/api/restart` | 重启服务 |

#### 12.5 配置管理
| 方法 | 路径 | 描述 |
|------|------|------|
| POST | `/admin/api/announcement` | 更新公告 |
| POST | `/admin/api/banners` | 更新横幅 |
| POST | `/admin/api/ads` | 更新广告 |

#### 12.6 删除请求管理
| 方法 | 路径 | 描述 |
|------|------|------|
| POST | `/admin/api/deletion-requests/:id/approve` | 批准删除请求 |
| POST | `/admin/api/deletion-requests/:id/reject` | 拒绝删除请求 |
| POST | `/admin/api/deletion-requests/:id/ignore` | 忽略删除请求 |

#### 12.7 管理页面（HTML）
| 方法 | 路径 | 描述 |
|------|------|------|
| GET | `/admin/` | 仪表板 |
| GET | `/admin/errors` | 错误日志 |
| GET | `/admin/queue` | 队列管理 |
| GET | `/admin/deletions` | 删除管理 |
| GET | `/admin/tokens` | Token管理 |

### 13. 首页及其他 (`/`)

| 方法 | 路径 | 描述 | 认证要求 |
|------|------|------|----------|
| GET | `/` | 首页（HTML） | 公开 |
| GET | `/search` | 搜索页面（HTML） | 公开 |
| GET | `/privacy` | 隐私协议页面（HTML） | 公开 |
| GET | `/disclaimer` | 免责声明页面（HTML） | 公开 |
| GET | `/deletion` | 数据移除政策页面（HTML） | 公开 |
| GET | `/statistic` | 统计页面（HTML） | 公开 |

## 请求示例

### 登录
```bash
curl -X POST https://www.luogu.me/user/login \
  -H "Content-Type: application/json" \
  -d '{"token": "your_token_here"}'
```

### 获取统计信息
```bash
curl https://www.luogu.me/api/statistic
```

### 保存文章
```bash
curl https://www.luogu.me/article/save/12345678
```

### 查询任务状态
```bash
curl "https://www.luogu.me/task/query?id=task_id_here"
```

## 响应格式

所有JSON API都返回统一格式：

```json
{
  "success": true,
  "data": { /* 具体数据 */ },
  "message": "操作成功"
}
```

或错误时：

```json
{
  "success": false,
  "message": "错误描述"
}
```

## 认证方式

1. **Token认证**：用户通过 `/user/login` 接口使用Token登录，服务端设置cookie
2. **管理员权限**：需要Token具有管理员角色
3. **公开API**：无需认证即可访问

## 注意事项

1. 所有保存请求（`/xxx/save/:id`）都是异步的，会返回任务ID供查询
2. 管理API需要管理员权限，普通用户无法访问
3. 部分功能（如犇犇高级搜索）尚未完全实现
4. 项目使用TypeORM和Redis，确保相关服务正常运行

## 更新日志

- 2026-02-21: 创建API文档，基于项目代码分析
- 2026-02-22: 将错误的 `http` 修改为 `https`

---

*文档基于 `luogu-saver` 项目代码分析生成，实际API以代码为准。*