---
order: 5
title:
  zh-CN: 带下拉框的按钮
  en-US: Button with dropdown menu
---

## zh-CN

左边是按钮，右边是额外的相关功能菜单。可设置 `icon` 属性来修改右边的图标。

## en-US

A button is on the left, and a related functional menu is on the right. You can set the icon property to modify the icon of right.

```jsx
import { Menu, Dropdown, Button, message, Space, Tooltip } from 'antd';
import { DownOutlined, UserOutlined } from '@ant-design/icons';

function handleButtonClick(e) {
  message.info('Click on left button.');
  console.log('click left button', e);
}

function handleMenuClick(e) {
  message.info('Click on menu item.');
  console.log('click', e);
}

const menu = (
  <Menu
    onClick={handleMenuClick}
    items={[
      {
        label: '1st menu item',
        key: '1',
        icon: <UserOutlined />,
      },
      {
        label: '2nd menu item',
        key: '2',
        icon: <UserOutlined />,
      },
      {
        label: '3rd menu item',
        key: '3',
        icon: <UserOutlined />,
      },
    ]}
  />
);

export default () => (
  <Space wrap>
    <Dropdown.Button onClick={handleButtonClick} overlay={menu}>
      Dropdown
    </Dropdown.Button>
    <Dropdown.Button overlay={menu} placement="bottom" icon={<UserOutlined />}>
      Dropdown
    </Dropdown.Button>
    <Dropdown.Button onClick={handleButtonClick} overlay={menu} disabled>
      Dropdown
    </Dropdown.Button>
    <Dropdown.Button
      overlay={menu}
      buttonsRender={([leftButton, rightButton]) => [
        <Tooltip title="tooltip" key="leftButton">
          {leftButton}
        </Tooltip>,
        React.cloneElement(rightButton, { loading: true }),
      ]}
    >
      With Tooltip
    </Dropdown.Button>
    <Dropdown overlay={menu}>
      <Button>
        <Space>
          Button
          <DownOutlined />
        </Space>
      </Button>
    </Dropdown>
  </Space>
);
```
