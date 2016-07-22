---
layout: post
title: react-native 基础控件
comments: true
category: React Native
---

react-native 基础控件
1、ActivityIndicator
		
		1.<ActivityIndicator
          style={[styles.centering, styles.gray]}
          color="white"
        />
        2.  <ActivityIndicator
            style={[styles.centering]}
          />
          <ActivityIndicator
            style={[styles.centering, {backgroundColor: '#eeeeee'}]}
          />
          3.      <ActivityIndicator color="#0000ff" />
          <ActivityIndicator color="#aa00aa" />
          <ActivityIndicator color="#aa3300" />
          <ActivityIndicator color="#00aa00" />
          4.<ActivityIndicator
          style={[styles.centering, styles.gray]}
          color="white"
          size="large"
          animating=true
        />
        
        
2.DatePickerIOS

	1<DatePickerIOS
          date={this.state.date}
          mode="datetime"//date,time,datetime
          timeZoneOffsetInMinutes={this.state.timeZoneOffsetInHours * 60}
          onDateChange={this.onDateChange}
        />
        
3.ListView
最基本的使用方式就是创建一个ListView.DataSource数据源，然后给它传递一个普通的数据数组
		