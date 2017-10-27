###部分ocl：
###AuthController类约束
####注册前约束：
	context AuthController::doRegister(String:account,String:password,String:IDcard,String:workID) pre:
	!AccountDao::checkRegistered(account)||AccountDao::checkIDcard||AccountDao::checkWordID


####登录前约束：
	context AuthController::doLogin(String:account,String:password) pre:
	!@pre.checkSession()||AccountDao::checkRegistered(AccountDao::getAccount(account))


####登出约束:
	context AuthController::doLogout(String:uuid) post:
	!@pre.checkSession()||AccountDao::checkRegistered


###SearchController类约束
	context SearchController::getRoomByHotel(Hotel:hotel) inv:
	HotelDao.checkHotelIsExisit(hotel)

	context SearchController::getHotelById(int:id)  inv:
	HotelDao.getHotelById(id)!=null

	context SearchController::getUserById(int id) inv:
	UserDao.getUserById(id)!=null

	context getOrderByUser(User:user) pre:
	UserDao.getUserById(user.id)!=null||@pre.checkSession()==user

	context getOrderByHotel(Hotel:hotel) pre:
	HotelDao.getHotelById(hotel.id)!=null||@pre.checkSession()==hotel.user

###ManagerController类约束
	context deleteOrder(Order:order) pre:
	@pre.checkSession()==order.user

	context bereaveUser(User:user)	pre:
	AccountDao::isManager(@pre.checkSession())||UserDao::getUserById(user.id)

	context bereaveHotel(Hotel:hotel)	pre:
	AccountDao::isManager(@pre.checkSession())||UserDao::getUserById(hotel.user.id)

	context passRegister(Hotel:hotel)	pre:
	AccountDao::isManager(@pre.checkSession())||!HotelDao.getHotelById(hotel.id)

	context getComplaintByHotel(Hotel:hotel)  pre:
	AccountDao::isManager(@pre.checkSession())||!HotelDao.getHotelById(hotel.id)

###MessageController类约束
	context MessageController::sendMessage(User:user)  pre:
	UserDao::getUserById(user.id)!=null

	context MessageController::sendMessage(Hotel:hotel)	pre:
	HotelDao::getHotelById(hotel.id)!=null

	context getMessageById(ind id) pre:
	AccountDao::isManager(@pre.checkSession())

	context getMessageByUser(User:user) pre:
	@pre.checkSession().id==user.id||AccountDao::isManager(@pre.checkSession())


	context getMessageByHotel(Hotel:hotel)	pre:
	@pre.checkSession().id==hotel.user.id||AccountDao::isManager(@pre.checkSession())