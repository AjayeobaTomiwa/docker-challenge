FROM node:latest

# create work directory
WORKDIR /app

COPY . /app

# install app dependecies for frontend
RUN npm install

# expose dev server port
EXPOSE 5173

# run dev server using npm
CMD ["npm", "run", "dev", "--", "--host"]