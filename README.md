## 1. main.ts (애플리케이션 진입점)
   - NestJS 애플리케이션을 실행하는 역할.
   - bootstrap() 함수에서 애플리케이션을 초기화.

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

## 2. app.module.ts (최상위 모듈)
   - 애플리케이션의 핵심 모듈.
   - 컨트롤러, 서비스 등을 모듈로 등록.

```
import { Module } from '@nestjs/common';
import { UserController } from './user.controller';
import { UserService } from './user.service';

@Module({
  controllers: [UserController],
  providers: [UserService],
})
export class AppModule {}
```

## 2-1. Module
   - NestJS 애플리케이션을 구성하는 기본 단위.
   - 관련된 컨트롤러, 서비스, 기타 기능을 하나의 모듈로 묶음.
   - @Module() 데코레이터를 사용하여 정의.

## 3. Controller
   - 클라이언트의 요청을 받아서 처리하는 역할.
   - @Controller() 데코레이터를 사용하여 정의.
   - @Get(), @Post(), @Put(), @Delete() 등의 데코레이터를 사용하여 라우트를 설정.

```
import { Controller, Get } from '@nestjs/common';

@Controller('users') // /users 경로로 들어오는 요청 처리
export class UserController {
  @Get()
  getUsers() {
    return '유저 목록';
  }
}
```

## 4. Service
   - 비즈니스 로직을 처리하는 역할.
   - @Injectable() 데코레이터를 사용하여 의존성 주입 가능.
   - 컨트롤러에서 호출하여 데이터를 가공하거나 데이터베이스와 상호작용.

```
import { Injectable } from '@nestjs/common';

@Injectable()
export class UserService {
  getUsers() {
    return ['유저1', '유저2', '유저3'];
  }
}
```

## 5. Class
  - NestJS에서는 컨트롤러, 서비스, 엔터티 등 대부분이 클래스로 정의됨.
  - 객체지향적인 개발을 가능하게 함.

## 6. @Injectable() (의존성 주입)
   - 서비스나 특정 클래스를 다른 곳에서 사용할 수 있도록 주입하는 기능.
   - @Injectable() 데코레이터를 추가하면 NestJS에서 자동으로 의존성을 관리.

```
import { Injectable } from '@nestjs/common';

@Injectable()
export class UserService {
  getUser() {
    return '유저 정보';
  }
}
```
