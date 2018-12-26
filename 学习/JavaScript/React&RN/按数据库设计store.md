### 按照数据库设计state
```
// 帖子state
let posts = {
	// 以id为key，保存全部post详细信息到一个无序map中
	byId: {
		f32413fdsafkjfjdlks: {
			id: 'f32413fdsafkjfjdlks',
			title: 'title',
			...
		}
		...
	},
	// 帖子列表，有序数组，只保存帖子的ids
	allIds: ['f32413fdsafkjfjdlks', 'h4ewfdsaf3g5y5drfecv']
}

// 帖子评论
let comments = {
	// 评论属于某个帖子
	byPost: {
		// 帖子id: [评论ids]
		f32413fdsafkjfjdlks: ['e2uojfdisioy982', 'feiowyiqy389f']
	},
	// 评论详情
	byId: {
		e2uojfdisioy982: {
			id: 'e2uojfdisioy982',
			...
		},
		...
	}
}

// 保存登录信息
let auth = {
	userId,
	username,
	token,
	...
}

// 保存用户信息
let users = {
	byId: {},
	allIds: []
}

let ui = {
	addDialogOpen: true,
	editDialogOpen: true
}

let app = {
	// 全局错误信息
	error: null, 
	// 当前应用中正在进行的API请求数
	requestQuantity: 0, 
}

// reducer
const byId = (state, action) => {
	if (action.type === types.UPDATE_POST) {
		return {
			...state,
			// !!!重点!!!
			[action.post.id]: action.post
		}
	} else {
		return state
	}
}


                      